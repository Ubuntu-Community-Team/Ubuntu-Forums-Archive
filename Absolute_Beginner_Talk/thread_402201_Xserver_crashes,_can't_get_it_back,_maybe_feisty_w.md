---
title: "Xserver crashes, can't get it back, maybe feisty will work"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by sneffers on 2007-04-05
Hi I need some help. My xserver just crashed so now all I have is command line. I was trying to fix my xserver but I couldn't. Someone said feisty might help my other problems. How do I do it from command line. If I run the upgrade manager, it says can't run gk something. I think it means it can't run anything with graphics because my xserver is down. can someone pleas help me?

---

### Post by zvacet on 2007-04-05
```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by sneffers on 2007-04-05
I'v done that like three times but it still doesn't work. After I do taht my xorg.conf file don't even have anything written in it.

---

### Post by brentoboy on 2007-04-05
if you want to  go to feisty...

```

sudo nano /etc/apt/sources.list

```

change all the edgy's to fiesty

ctrl + x  to close (tell it to save when it asks)

```

sudo apt-get update
sudo apt-get dist-upgrade

```

Go to lunch, come back in an hour

reboot your system  (press ctrl + alt + delete, will tell they system to shutdown nicely and reboot)

if you are still in text mode at that point, post again, and we can sort out your video driver from the command prompt.

---

### Post by sneffers on 2007-04-05
Umm I did that, but...I don't even have the command line now! All i have is this error I have had before taht says something like follows:
 can't grab port: 0x0
opl3sa-2
yamaha opl3-sa: soundcard not found or device busy


and that's all I remeber of it. I only made it worse.

---

