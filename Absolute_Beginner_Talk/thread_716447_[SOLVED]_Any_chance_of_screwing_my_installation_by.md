---
title: "[SOLVED] Any chance of screwing my installation by running this command ?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Google Spider on 2008-03-05
Hi,
I just read [[COLOR="Blue"]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=715551") thread. I have the same graphics card but I am on Edubuntu 7.10. I think I will try out those commands today
```

sudo apt-get install xorg-driver-fglrx
sudo apt-get install xserver-xgl

```
 
But I want to know if there are any chances of screwing the GUI ? 
If the GUI gets screwed, then what is the procedure to get the things back to normal by removing XGL (uninstallation procedure from command line ) ?

There is no important data on my drive so I don't mind completely reformatting, in case I screw things.
Oh, and I forgot to mention-- I'm a n00b. Have been using Edubuntu for the last three months.
Any advice is appreciated.

Thank you.:)

---

### Post by santiagoward2000 on 2008-03-05
> **Google Spider said:**
> Hi,
I just read [[COLOR="Blue"]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=715551") thread. I have the same graphics card but I am on Edubuntu 7.10. I think I will try out those commands today
```

sudo apt-get install xorg-driver-fglrx
sudo apt-get install xserver-xgl

```
 
But I want to know if there are any chances of screwing the GUI ? 
If the GUI gets screwed, then what is the procedure to get the things back to normal by removing XGL (uninstallation procedure from command line ) ?

There is no important data on my drive so I don't mind completely reformatting, in case I screw things.
Oh, and I forgot to mention-- I'm a n00b. Have been using Edubuntu for the last three months.
Any advice is appreciated.

Thank you.:)

Hi!
I don't think so. I have an ATI Radeon Xpress 200m too and worked great for me. :D
Just in case you want to disable XGL, enter:
```
mkdir ~/.config/xserver-xgl
touch ~/.config/xserver-xgl/disable
```
Good luck!

---

### Post by Google Spider on 2008-03-06
Thanks it worked!

---

### Post by santiagoward2000 on 2008-03-06
> **Google Spider said:**
> Thanks it worked!

You're welcome!

---

