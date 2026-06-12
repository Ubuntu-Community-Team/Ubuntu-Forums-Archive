---
title: "No Users Information set up"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by pibob314 on 2007-09-15
Hello.
I've recently installed Ubuntu Ultimate 1.4 to run as a virtual machine on my Windows computer. Unfortunately, the first time I ran it, it didn't go through a first-time boot procedure so that I could set up a user name and password. Instead it went straight to the login in screen where I could not login due to lack of the above. 
If anyone has any suggestions on the best way to tackle this problem please let me know. I'm not the most computer savvy person in the world so "be gentle". 

Thanks

---

### Post by SOULRiDER on 2007-09-15
Check this out:
[http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/](http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/)

You will have to reboot in revoery mode and follow those steps. Make sure though, that when you create it will the adduser <name> command, you will have to add your user to the wheel group. Type: adduser --help (yes, two -'s) for mor einfo on how to use that command. If you run into any troublr just ask here.

---

