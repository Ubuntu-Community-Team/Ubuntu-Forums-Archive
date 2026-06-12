---
title: "How to edit /etc/fstab in recovery mode??"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by fer5437 on 2006-05-22
I mounted the wrong partition. Before that my /etc/fstab look like this

> 
#/etc/fstab: static file system information
#
#file system

/dev/hda1     /          ext3       defaults       errors=remount -ro     1
dev/hdb1      /home   ext3       defaults        0              2
dev/hdb2      /usr      ext3       defaults        0              2
dev/hdb3      /var      ext3       defaults        0              2

/dev/hda2     /none    swap      sw               0              0


But after I edit it, it become like this

> 
#/etc/fstab: static file system information
#
#file system

/dev/hda1     /          ext3       defaults       errors=remount -ro     1
/dev/hdb1      /home   ext3       defaults        0              2
/dev/hdb2      /usr      ext3       defaults        0              2
/dev/hdb3      /var      ext3       defaults        0              2
/dev/hdb5      /usr      ext3       defaults        0              2

/dev/hda2     /none    swap      sw               0              0


Then after I reboot I have problem to boot up. Now I boot in with recovery mode. So the problem now is how can I edit the /etc/fstab?? I feel so stupid to that mistake. Please help

---

### Post by Ecthelion on 2006-05-22
Doesn't the normal
```
sudo nano /etc/fstab
```
works?

I'm actually not sure you even need the sudo in save mode...


EDIT: If nano doesn't work you can also try pico or another command-line editor

---

### Post by fer5437 on 2006-05-22
One more thing, I try to get the tutorial "nano" from the internet but I cant really understand how to use it. Can you teach me how to save in nano? And also quit from "nano".

Thx a lot for helping.

---

### Post by Eric_T on 2006-05-22
You just edit like in any other text editor. To exit and save, press Ctrl+X, then Enter.

---

### Post by fer5437 on 2006-05-22
Thank a lot too all. You guy safe my ubuntu. My problem solve and now can boot up already. Thank you.

---

