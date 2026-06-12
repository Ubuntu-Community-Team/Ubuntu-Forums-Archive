---
title: "Dapper Drake 6.06 Resolution"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-07-03
Here is my question, I was trying to install Dapper on an HP computer I had at home.  Well, first it wouldn't install for some crazy reason. I would run the install and it would run for a few second then reboot itself.  So then I decided to run the live CD and try to install it from there.  Well, I got it to run live and when I go to install it the resolution size is so big I can't see my options on the install.  I went to the preferences and to screen resolultion but it only has one option of 600x450 something like that.  There is no other option, but I know there is a way to change it from the command line.  Can anyone guide me in the right direction?  Any advice will be helpful.:confused:

---

### Post by Jagot on 2006-07-03
Try:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by wolfmaniac on 2006-07-03
add ur resolution in

/etc/x11/xorg.conf  (as root)

restart x server ,or preferably reboot.

---

### Post by NeoGreen on 2006-07-05
Okay, I'll try it thanks.:)

---

### Post by NeoGreen on 2006-07-08
If this is a new install, will I be able to add that resolution?  I've heard that I woud have to input a repository for it to work.  I really don't know, I hope this isn't a dumb question.:confused:

---

### Post by Apple 101 on 2006-07-08
Try Jagot's reply first.

---

### Post by NeoGreen on 2006-07-09
Okay, I'll try it. :D

---

