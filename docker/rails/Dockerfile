FROm ruby:2.2.3
RUN apt-get update -qq && \
    apt-get install -y apt-utils \
                       build-essential \
                       libpq-dev \
                       nodejs \
                       mysql-client
RUN mkdir /app
WORKDIR /app
ADD ./src/Gemfile /app/Gemfile
ADD ./src/Gemfile.lock /app/Gemfile.lock
RUN bundle install -j4
ADD ./src /app

EXPOSE 3000
# 次の行は本番環境でしか実行されない
CMD ["unicorn", "-p", "3000", "-c", "/app/config/unicorn.rb", "-E", "production"]
