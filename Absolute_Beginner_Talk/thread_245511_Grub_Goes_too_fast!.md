---
title: "Grub Goes too fast!"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by shawn524 on 2006-08-27
Hi, I set it up so that grub would load windows XP MCE first, and do it quickly. So my problem is, i set the default time to 0 and now i cant get into linux. Any suggestions?

---

### Post by bodhi.zazen on 2006-08-27
Boot with the live cd.

Edit /boot/grub/menu.lst

Change```
 timeout 0
```

To

```
 timeout 10
```

Reboot (to HD).

Should be good o go.

---

### Post by shawn524 on 2006-08-28
Am I missing something in the downloads menu? where is the live CD option. Oh and thatnks for the advice, don't know why i didn't think of that.

---

### Post by shawn524 on 2006-08-28
Oh nevermind. Guess I just need to read more. Thanks.

---

### Post by bodhi.zazen on 2006-08-28
Go to this page:
[http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/](http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/)

click the "PC (Intel x86) desktop CD".

AKA ubuntu-6.06.1-desktop-i386.iso

This is a live CD.

You could use almost any live Linux or rescue CD if you have something on hand other then Ubuntu.

---

