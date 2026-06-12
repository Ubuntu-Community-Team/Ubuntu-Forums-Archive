---
title: "php sendmail or..."
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by dpan on 2006-10-24
I have been playing with ubuntu for a week and love it. The reason I installed it is becuase I write alot of php and windows does some very strange things with php...

I installed or should I say tried to install several other flavors of linux with no happyness.... (my notebook is very ubscure) Ubuntu ROCKS!!

any how I have gotten evrything setup and working great, except for the one thing. My php script needs to send mail, I need to test it before I go upload  the script to my www server.

The problem is I want to use mail() function for testing/debuging only and the last thing I want is an open relay..... I also noticed others have had problems with sendmail messing up and hanging boot..... (Me newbbie.. That would destroy my week)


I also looked in Add/Remove programs and can't find sendmail.

So to my question what should I install to act as send mail, how do I install & configure it....

Thanks David.....

---

### Post by mssever on 2006-10-25
postfix is the most common mailer nowadays. It comes with a sendmail wrapper so that PHP doesn't know the difference. I think that the default install is fairly secure, but I really don't know enough about postfix to be able to help you there. I suggest installing postfix and reading the man page.

---

