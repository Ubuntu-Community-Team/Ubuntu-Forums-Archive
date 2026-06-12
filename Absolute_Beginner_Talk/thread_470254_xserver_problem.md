---
title: "xserver problem"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by KalessArtennis on 2007-06-10
I have just installed the "NVIDIA Linux x86 100.14.09 Device Driver" and now the xserver wont start.

I am using Ubuntu 7.04 and my graphics card is a NVIDIA 7300 PCI

Attached is the xserver log.

All help is appreciated

Thanks
Kaless

---

### Post by Rocket2DMn on 2007-06-10
```
sudo dpkg-reconfigure xserver-xorg
```
will help you to reset your xorg.conf file

---

### Post by KalessArtennis on 2007-06-10
thanks rocket but it didnt seem to work.

after choosing my colour depth it came up with a message saying it was going to overwite the file and then wouldnt let me continue the configuration.

I rebooted and it still says no screens found in the xserver error/

Any ideas?

---

### Post by Rocket2DMn on 2007-06-10
Can you post your /etc/X11/xorg.conf file?  Hopefully this can give us some insight into what's going on.

---

### Post by KalessArtennis on 2007-06-10
here it is

thanks this is my first day using ubuntu

---

### Post by KalessArtennis on 2007-06-10
here

---

### Post by Rocket2DMn on 2007-06-10
Unfortunately, I don't have the benefit of experience with NVIDIA cards, as I have an ATI in my laptop.  
The xorg.conf file has backups in the same directory in the form: xorg.conf.YearMonthDayTime (I think it's Time anyway).  You can try restoring a backup from before you tried to upgrade your driver.  Give this a shot.

If it doesn't work, you may need to keep browsing around for solutions or get ahold of somebody with more NVIDIA experience.
Good luck, buddy!

---

### Post by KalessArtennis on 2007-06-10
ah well, restoring from the backups didn't work, looks like im going for a full reinstall.

its undoubtably the kernel that the driver compiled that is the problem.   Probably doesnt like my graphics card (it is one of the cheaper models).

thanks for the help neways rocket, i will probably hold back on installing the driver in the future untill nvidia has worked out some of the bugs.

---

