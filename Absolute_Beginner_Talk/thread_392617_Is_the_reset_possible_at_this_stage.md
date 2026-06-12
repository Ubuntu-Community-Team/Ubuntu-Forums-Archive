---
title: "Is the reset possible at this stage?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by donamai on 2007-03-24
Hi,

I am curious about resetting the system again. I had a problem with the xorg file and now that I looks at the file all the settings I have put in  are just generic as if the drivers are not present .

I was wondering if it is possible to reset the system back to the way it normally ran before any error or better yet is there a command line for the system to rediscover the devices attached to the computer again as if it did the first time if booted from the first system installation?

In other words, I want to make sure all the files are the way they are supposed to be. I just installed the OS and updated to all the available updates so I am not sure if even going back to the first installation setup will work.

What do you think?

---

### Post by zorkerz on 2007-03-24
The only way i know of doing this is doing a clean install.  I agree with you that this would be a very handy functionality to have. There are times when things have been changed that you just want to be able to start at a default again. If all you are trying to do is make a new xorg.conf file then type this.
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by annda on 2007-03-24
if you just want to reset Xorg, try this command:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by zorkerz on 2007-03-24
what is the -phigh for i have no used it before?

---

### Post by zekopeko on 2007-03-24
man dpkg-reconfigure says :

-pvalue, --priority=value
           Specify the minimum priority of question that will be displayed.  dpkg-reconfigure normally shows low priority
           questions no matter what your default priority is. See debconf(7) for a list.

i'm guessing that it means that important question come first

also you could make a default backup when installing for the first time.

i think that it was something as easy as ziping the ' / ' path minus the proc and someother folders with the processes.

here is the thread. pretty simple.

[http://ubuntuforums.org/showthread.php?t=35087&highlight=howto+backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=howto+backup)

---

