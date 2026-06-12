---
title: "Found a way to enable the 'su' command"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-01-13
Hi just a quick post reguarding the 'su' command... This has already bound to have been discovered I know but I've read many articles on the internet saying the 'su' command couldn't be used with Ubuntu but all I did was type the command *sudo passwd; then typed in my new UNIX password* Then I could use the su command using that pass... I'm just abit puzzled??? anyway hope this helps people...:)

---

### Post by Pobega on 2007-01-13
As far as I know you just enabled the root account, which is not recommended. If you wanted to use something like su you could have done > *sudo -i* which logs you in as root like sudo, but without **actually** enabling the root account.

---

### Post by Sef on 2007-01-13
Actually it is safer not to use root; hence the reason for locking it and using sudo instead.  Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo") for more information.

---

