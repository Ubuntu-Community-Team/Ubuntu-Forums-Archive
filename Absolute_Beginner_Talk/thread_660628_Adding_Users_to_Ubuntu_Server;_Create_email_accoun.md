---
title: "Adding Users to Ubuntu Server; Create email account, too?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by BlueKnight84 on 2008-01-07
Hello.  I was wondering if by adding a user to my Ubuntu server if that will give the user an email address, for example, if the new user was named *dude*, and my domain name was *coolguys.com*...

[INDENT]**dude@coolguys.com**[/INDENT]

Does creating users work like that?  I have Ubuntu 7.04 and I'm running Sendmail as my mail program.  I am a total Ubuntu noob, so take it easy on me!

Thanks in advance!

---

### Post by Hospadar on 2008-01-07
I think that sendmail would pick up new users as new email addresses, but that might not be the case.

As for adding users by command line you'll want to use adduser.  you can do a "man adduser" to get info about it's options.  You'll probably also need to do some further manual configuration (adding users to groups, giving a user sudo privileges if you want them to have them, etc) I'm not really sure what all adduser does, I bet it could handle this stuff though

---

### Post by hyper_ch on 2008-01-07
Hmmm, I don't think it does that automatically...

But then I always used a control panel for my server...

---

