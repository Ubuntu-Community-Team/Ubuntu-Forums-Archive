---
title: "Doing things on entering wrong passwords..."
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by tzembi on 2007-08-13
Hi there,

Is there any easy way to run a script (eg: sending a mail, unmounting drives, shutting down the pc, etc...) if a Password attempt had been unsuccessful for the third, fourth, ...  time ?

I know auth.log is the place to look for failed authentication but i ve got no idea how to automagically do something if the failed authentications exceed a certain threshold.

Thanks for any ideas,

TZembi

---

### Post by kidders on 2007-08-14
Hi there,

In principle, doing something like this is *extremely* unwise, since it essentially allows strangers to cause possibly complex (and potentially exploitable) things to happen by remote control ... a privilege normally reserved for authenticated users.

If it's something you really want to do, you could certainly create a short script to count failure messages in your system logs, and run things. Do you have any particular language in mind?

---

### Post by ddrichardson on 2007-08-17
Some of what you want is handled by login and faillog. I'll have a look into how the mail notification works because I haven't used it in ages. Slackware has this set by default so that failed login attempts are mailed to the root user.

---

### Post by tzembi on 2007-08-25
Thanks for the Info everyone. I want to use this to send a notification of failed Password trys to several Email accounts and run a script to identify the rudimetary source of the login (console, remote etc..). This could be a cronjob or anything, really. Do you have any shellscript examples for something like this ?

Thank you,
TZembi

---

