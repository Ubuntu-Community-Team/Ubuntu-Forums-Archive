---
title: "Why is Ubuntu freezing?"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by xjosie729 on 2007-02-11
I heard before that Ubuntu is pretty fast, better than Windows, but it seems that I cannot open more than 3 windows or more than 5 tabs in Firefox or else it'll freeze. That's not the case with my Windows installation. I have a 27 GB partition for Ubuntu and 256MB of RAM, which should be enough for it to run smoothly, right? I don't know what's wrong with it.

---

### Post by rabid emu on 2007-02-11
Strange problem.  During one of these 'freezes', can you access a TTY console?  (press ctrl + alt +f1, it should switch to a terminal).  If you can indeed access a terminal, then the OS itself is not freezing, just the X server.

---

### Post by nickoli_02 on 2007-02-11
Is some process hogging a bunch of system resources? I had this problem before when I installed the newest version of the ATI video card drivers. Try typing "top" at the terminal to see if anything is consuming a lot of resources. If you don't see anything unusual then open a lot of tabs in firefox or whatever slows the system down and then type "top". Worth a shot.

---

### Post by xjosie729 on 2007-02-16
Actually, it's not FREEZING, it's just SO slow that it's almost like freezing. It takes 5 minutes for me to get to the close button of firefox, and another 10 minutes for it to display the force quit dialog, so I just force it to turn off.

---

### Post by jordanmthomas on 2007-02-16
can you post the output of 
```
free -m
```
My guess is you have no swap partition.

---

### Post by xjosie729 on 2007-02-18
I did make a swap partition, but for some reason, Ubuntu reformatted it to an unknown type. I tried changing it before, but it totally messed up my computer and I had to reinstall everything. Here are the screenshots! I have Ubuntu installed on hda5 and the swap partition *should* be on hda6.

---

### Post by mcduck on 2007-02-18
Try running 'sudo swapon -a'
then check the swap with 'free -m'

If that doesn't work 'sudo mkswap /dev/hda6' and then again 'sudo swapon -a' and test again with 'free -m'

Also check that you have correct entry for swap in /etc/fstab.

---

### Post by xjosie729 on 2007-02-18
> **mcduck said:**
> Try running 'sudo swapon -a'
then check the swap with 'free -m'

If that doesn't work 'sudo mkswap /dev/hda6' and then again 'sudo swapon -a' and test again with 'free -m'

Also check that you have correct entry for swap in /etc/fstab.

Thanks, that worked! Now I just have to see if it is still slow...

---

### Post by xjosie729 on 2007-02-18
Thanks everyone! It's not slow anymore!

---

### Post by mcduck on 2007-02-18
Great that you got it working :)

BTW, with only 256 MB of ram you could try XFCE4 desktop, it should work noticeably faster than Gnome. just do 'sudo apt-get install xubuntu-desktop' and then you can choose XFCE from the login screen..

---

