---
title: "user session time restriction"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by bluefrog on 2006-05-19
here is the following scenario:

1) Joe is authorized to log on (gdm) and use the computer everyday only from 3pm to 5pm.

2) If Joe is logging on at 4:45pm he must be disconnected at 5pm.

Adding the following line in /etc/pam.d/common-account:
account required pam_time.so

and adding the following line in /etc/security/time.conf:
gdm;*;joe;Al1500-1700

Now joe cannot log on before 3pm and after 5pm. Fine (although a strange behavior happens, see the comment strange behavior below...)

BUT if he logs on at 4:45 pm, he can go on and on using the computer past 5pm (see main problem at the bottom of this thread...)

STRANGE BEHAVIOR:
I modify the /etc/pam.d/common-account using my ubuntu admin account (not root). 
As soon as I implement "account required pam_time.so" my admin account cannot use any more graphical frontend where gksudo is invoked. Indeed from now on if I call synaptic gui, it tells me the password is incorrect (logs shows only pam_time can't get the tty name, sudo authentication failure).
Meanwhile sudo in console still works fine. I do a sudo -k to force sudo in console to ask me again for password.
As soon as I comment #account required pam_time.so" gksudo accepts my password again.

Back to time restriction problem.

I tried using timeoutd as well but so far I only manage to make it work so joe has so many minutes allowed per connection and per day.

Timeoutd seems to have a slight problem as well with the syntax in /etc/timeouts. If I change /etc/timeouts with
Al1700-1500:*:joe:*:NOLOGIN
then do sudo /etc/init.d/timeoutd restart, it restarts fine but after a (very short) while it receives a SIGTERM signal. Apparently even if man timeouts says we can write like this it seems to dislike Al1700-1500. If I only write Al:*:joe:*:NOLOGIN, it works and joe is disconnected one minute after he logged in.

MAIN PROBLEM:
How to have joe be disconnected automatically (with a warning eventually) when he reaches his time range limit? And preferably joe will not be able to logon at all (not logging on and disconnected after one minute)

thanks
James

---

### Post by jasay on 2006-05-19
Couldn't you write a script to check if Joe is logged in and log him out.  Then set up [cron]("https://wiki.ubuntu.com/CronHowto") to run the script everyday at 5PM?

---

