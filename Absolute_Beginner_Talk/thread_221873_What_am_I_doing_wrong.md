---
title: "What am I doing wrong?"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by dragon1964m on 2006-07-24
I want to mount a local Windows XP partition. My second install of Ubuntu did this automatically. This install and another did not. I am following an O'Reilly "Ubuntu Hacks" book. I type $ /etc/fstab  and I get; permission denied. I type $ sudo /etc/fstab  and get; cannot find file. I am the only user account and I have full admin rights. Why does this happen? What can I do to resolve this annoyance? And how do I mount /dev/hda1  my win XP partition?

Oh, that "permission denied" and "cannot find" error have popped up more than once. Do I need to change a setting somewhere?

And the install issue; I read that Ubuntu 6.06 should mount other partitions automatically. If this is true, I have had 2 fails, should I "bug report" or am I missing something there too?

---

### Post by aysiu on 2006-07-24
```
sudo nano -B /etc/fstab
``` Actually, full instructions are here: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by MrHorus on 2006-07-24
> **dragon1964m said:**
> I type $ /etc/fstab  and I get; permission denied. I type $ sudo /etc/fstab  and get; cannot find file. 

Yup, of course you will - you are just saying "/etc/fstab" to the shell and the shell is going "alright, the fstab... so er... what about it?" since you haven't told the shell what command you wish to use.

Precede "/etc/fstab/" with the text editor of your choice as suggested previously and you should then be able to open it and edit it.

---

