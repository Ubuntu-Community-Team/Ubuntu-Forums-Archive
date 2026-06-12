---
title: "Should I Change default Root Password"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2008-03-25
When I installed Ubuntu 7.10  I was just asked to set my own password that I would
use to logon and to enter during admin tasks such as installing software.  I'd like to
know what the Root password would be, Is it the same as my log on?  If so shouldn't
I change it for security reasons?  What do you guys recommend?

Thank you  :)

---

### Post by dannyboy79 on 2008-03-25
there is no default root password  set in Ubuntu by default. there's only your username and your usernames password and due to you being part of the admin group, you can use sudo, which then requires you to enter YOUR password. if you really want to set the root password you can with this command

sudo passwd root

then enter YOUR password once, then it'll ask you what you want for the new ROOT password. Don't ever forget this though. You don't ever need to login as root so I wouldn't do this, it's not required when you have sudo.

---

### Post by Mustard on 2008-03-25
This link explains some of the concepts behind using sudo...


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by neumann on 2008-04-06
Thanks very much for the answers from Dannyboy79 and Mustard this has helped me a lot.

---

