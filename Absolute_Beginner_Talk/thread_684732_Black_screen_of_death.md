---
title: "Black screen of death"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by NStoker on 2008-02-01
Hey, I just reciently got ubuntu, and I love it!  when i changed my video setting, or graphic setting (I can't remeber whichc one) their were a few options,  None,  Normal, High(something like that) and custom, So i pressed custom and it told me to restart my sysytem. when my system started back up it did the ubuntu loading screen then goes to a black screen and says "Cannont Display This Video Mode"   one of my friends told me to do this under the recovery mode to fix it,  sudo dpkg-reconfigure xserver-xorg       It went through like 20 steps and still after that it still didnt' work.  So what can i do?????? My AIM is almost always running so if u want to help me that way just IM me.  the AIM adress is:  skiman13193

Thanks!:)

Ps: I have the Nvidia Geforce 6800 video card

---

### Post by NStoker on 2008-02-01
bump, Anyone got any ideas? I'm helpless?

---

### Post by NStoker on 2008-02-01
anybody?????:confused:

---

### Post by jan quark on 2008-02-01
do you get to the login screen?

if yes try to change the session to gnome session

---

### Post by ~LoKe on 2008-02-01
Try a small variation...
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
But I hope your friend told you that you have to chroot into the old installation to make the changes if you're using a LiveCD.

So, while using the LiveCD, type this:
```
sudo fdisk -l
```
Find out which partition has your Ubuntu installation on it (should look something like /dev/sda1) and chroot into it.

```
sudo mkdir /media/gutsy
sudo mount /dev/sda1 /media/gutsy
```
```
sudo chroot /media/hardy su
```
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by SunnyRabbiera on 2008-02-01
yeh you probably screwed something up there, gutsy has a lot of issues like this.

---

### Post by NStoker on 2008-02-01
Thanks guys! I got it to work! Thanks

---

