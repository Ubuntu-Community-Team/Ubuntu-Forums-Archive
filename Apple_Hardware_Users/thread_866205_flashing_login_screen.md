---
title: "flashing login screen"
date: 2008-07-21
forum: Apple Hardware Users
---

### Post by Berthor on 2008-07-21
I am on a macBook pro, and i have VM fusion running an install of ubuntu 7.10.  I had to go through 2 rounds of updates.  the first round wasn't a problem. however, after doing the second round of updates. ubuntu will start up all the way to the login screen.  then it will basically, reload/flash over and over again.  always moving the mouse to the center of the screen, and basically always in a state of thinking (round circular cursor).  I can boot the system in the recovery  mode, but I don't know how to bypass the login screen in normal mode.  I was hoping that I could find some command line commands that will enable me to bypass the login screen (seeing how i am the only one who uses this laptop), but I couldn't find anything.  

if anyone knows, you would be saving me the hassle of reinstalling from scratch.  (because I have an up and running project on it currently.)

Thanks in advance.

---

### Post by cyberdork33 on 2008-07-22
You can try reinstalling gdm. You should be able to do that in recovery mode using tools such as apt-get. You even might just try updating further from the commandline...

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

If you are concerned about your project files, boot into recovery mode and copy the files off the VM disk image.

---

