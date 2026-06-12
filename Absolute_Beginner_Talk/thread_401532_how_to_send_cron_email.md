---
title: "how to send cron email ?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by gotquestions on 2007-04-04
hi. for learning purposes i am trying to create an automated email send just for a specific day to my friend. on the linux prompt i did: crontab -e 
i get this screen and i typed in this

# m h  dom mon dow   command
  45  14 4   4   *     $HOME/www/test


i got an email shortly with something like this:
/bin/sh: /home/apple/www/test: Permission denied

i have a file called "test", where test is going to be the body of the email.
i looked at something on mail. (man mail)

anyhow my question is, how can i combine crontab and mail? can someone teach me how i can do this? im a beginner

---

### Post by chalex on 2007-04-04
The standard way to send mail from the command line is using the program called "mail".  It takes the subject and the destination address as arguments and then the body of the e-mail from stdin.  It looks like it's not included by default in Ubuntu (at least on my machine).  It is provided by the package called mailx.

"sudo apt-get install mailx"
"man mail"

As to your original question, $HOME/www/test is not an executable, so you get the error.  You want to write a bash script that goes something like this:
```

#!/bin/sh

mail -s "subject" address@to.mail  << MARKER
body of email goes here
MARKER

```

Then chmod +x this script and put the path to in into the crontab.

---

