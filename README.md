# crontab-tool

So in this challenge we’re going to learn about cron, how to configure it and we’re going to build a tool to decode it’s configuration: crontab (short for cron table).

So what does a crontab file look like? If I used it to send out the Coding Challenges newsletter at 9am on Saturdays, it would look something like this:

0 9 * * 6 <command to send Coding Challenges>
Which can be interpreted using the following:

# ┌───────────── minute (0–59)
# │ ┌───────────── hour (0–23)
# │ │ ┌───────────── day of the month (1–31)
# │ │ │ ┌───────────── month (1–12)
# │ │ │ │ ┌───────────── day of the week (0–6) (Sunday to Saturday;
# │ │ │ │ │                                           7 is Sunday on some systems)
# │ │ │ │ │
# │ │ │ │ │
# * * * * * <command>
There are also some extensions such as @yearly, @monthly, @daily and so on. For these fields the allowed values are:

Field Required Allowed values Allowed special characters Remarks Minutes Yes 0–59 * , - Hours Yes 0–23 * , - Day of month Yes 1–31 * , - ? L W ? L W only in some implementations Month Yes 1–12 or JAN–DEC * , - Day of week Yes 0–6 or SUN–SAT * , - ? L # ? L # only in some implementations

is then a wildcard, meaning all.
, separates items in a list, i.e. 1,3,5.

defines a range, i.e. 1-5.
/ specifies step values, i.e. /5 for every 5 minutes.

L stands for last, as in last day of the week.

W for a weekday in the day of the month field.

Use man on your system to dig into the full documentation.

Step Zero

In this step you decide which programming language and IDE you’re going to use and you get yourself setup with a nice new project.

You can develop your solution to this challenge as a command like tool, GUI or entirely as a frontend, web-based project. The last time I did it, I did it in TypeScript building a frontend in React and Material UI.

Step 1

In this step your goal is to build the user interface for your solution. You will want to accept from the user a cron expression of five fields, for example: 0 9 * * SAT.

Here’s my UI in React, I decided to add a table explaining (reminding) what each symbol means:

![img1](https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff16a331e-48d9-4588-a4b7-686922642187_904x492.png)

Step 2

In this step your goal is to validate the crontab expression and provide the user with an informative error if it is not valid.

This is a great step to practice TDD on. You can create a range of valid and invalid patterns then test your validation code.

Step 3

In this step your goal is to translate the expression into natural language. Many developers find the patterns somewhat cryptic so having a tool to translate them to natural language is useful.

![img2](https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F22c1d2ae-7101-465d-9984-f5014569cf31_886x139.png)

![img3](https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ffe904f9d-042d-465f-9a05-db8e3099bf4b_882x140.png)
