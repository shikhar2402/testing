# django-todo
A simple todo app built with django
resource "aws_cloudwatch_event_rule" "daily_schedule_rule" {
  name        = "glue-job-daily-schedule"
  description = "Schedule for Glue job"
  schedule_expression = "cron(0 12 * * ? *)"  # Daily at 6:00 PM IST (12:00 PM UTC)
}

resource "aws_cloudwatch_event_target" "trigger_glue_job" {
  rule      = aws_cloudwatch_event_rule.daily_schedule_rule.name
  target_id = "trigger-glue-job"
  arn       = aws_glue_job.example_job.arn
}
![todo App](https://raw.githubusercontent.com/shreys7/django-todo/develop/staticfiles/todoApp.png)
### Setup
To get this repository, run the following command inside your git enabled terminal
```bash
$ git clone https://github.com/shreys7/django-todo.git
```
You will need django to be installed in you computer to run this app. Head over to https://www.djangoproject.com/download/ for the download guide

Once you have downloaded django, go to the cloned repo directory and run the following command

```bash
$ python manage.py makemigrations
```

This will create all the migrations file (database migrations) required to run this App.

Now, to apply this migrations run the following command
```bash
$ python manage.py migrate
```

One last step and then our todo App will be live. We need to create an admin user to run this App. On the terminal, type the following command and provide username, password and email for the admin user
```bash
$ python manage.py createsuperuser
```

That was pretty simple, right? Now let's make the App live. We just need to start the server now and then we can start using our simple todo App. Start the server by following command

```bash
$ python manage.py runserver
```

Once the server is hosted, head over to http://127.0.0.1:8000/todos for the App.

Cheers and Happy Coding :)
