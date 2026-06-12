---
title: "sshfs: remote host has disconnected"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-09-04
I'm once again trying to get a good easy connection between two Ubuntu systems.
I have read some instructions and installed sshfs and added fuse to modules;
then I tried to mount:
sshfs 192.168.2.5:/home/ml3
where 192.168.2.5 is the inet address of the computer I want to connect to and ml3 is my username on the other computer, so it is my home directory I want to get access to.
1. Why do I always get "remote host has disconnected"?
Do I need to allow this computer here (192.168.2.4) to connect to that computer (192.168.2.5)? Where can this be done?
2. If I somehow get through this - can the same app (sshfs) be used to do the same mounting from a totally different place, where 192.168.2.5 won't be enough?

---

### Post by garretwp on 2006-10-30
I get the same error remote host has disconnected. Does anyone know what causes this and how to fix it?

- Garrett

---

### Post by sitedesign on 2006-10-31
did you install openssh-server on the computer that you are trying to connect to.

Try just a normal ssh connection to it first:
ssh 192.168.2.5 -l username
If that fails then the openssh-server is not running on the remote computer.

Oh and yes the 192.168.2.5 can also be a public IP on the internet. I think you can even use some port forwarding to make it look a bit more secure but also allowing you to connect to several computers inside a network which only has one public IP.

---

### Post by jinx099 on 2006-11-03
I'm having the same problem, and ssh server is definitley running on my server.

---

### Post by jetpeach on 2006-11-05
see this thread
[http://www.ubuntuforums.org/showthread.php?t=287710&highlight=sshfs](http://www.ubuntuforums.org/showthread.php?t=287710&highlight=sshfs)
the sshfs command should have the directory it's being mounted to in it and the hone being mounted after the ip of the computer (the 1st post on this thread does not.)
the error usually means the target directory or the source directory cannot be found (somebody was saying hopefully they'll change the error message...)

---

### Post by xeth_delta on 2007-11-16
The last reply to this thread is more than a year old, but for what it's worth, I also have been having problems at mounting remote directories through sshfs. It turned out to be a problem with the .cshrc file in my home directory on the remote server. After making a slight change in that file I am finally able to use sshfs.
More information on [http://openssh.org/faq.html#2.9]("http://openssh.org/faq.html#2.9").

Xeth

---

