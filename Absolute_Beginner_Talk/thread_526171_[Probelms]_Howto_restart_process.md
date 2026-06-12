---
title: "[Probelms] Howto restart process"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by dkone on 2007-08-15
[SOLVED]
The process is not located there. It's located in /etc/init.d
[/SOLVED]


HEy guys,..

I want to restart the SSH deamon, after editing the sshd_config. I am using putty, accessing the server
remotely with root. However, if i do:

*/usr/sbin/sshd restart*

All I get is:

*Extra argument restart.*

What is the problem here? (I know it's me,...but what am I doing wrong?)

Thanks for your help

---

### Post by hausman on 2007-10-16
Not to mention, for the assistance of other folks new to this:

/etc/init.d/ssh restart

(note the lack of "d" in ssh)

---

