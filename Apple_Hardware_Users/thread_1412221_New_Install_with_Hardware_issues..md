---
title: "New Install with Hardware issues."
date: 2010-02-20
forum: Apple Hardware Users
---

### Post by DeadCthulhu on 2010-02-20
Hello, I am new to Ubuntu, and new to this forum as well, any help you could offer would greatly be appreciated.

I installed a new, clean hard drive into my old iMac G5, and decided to finally set up a linux machine, I installed Ubuntu 9.10 with the 64bit mac software, and the instal went very smooth, however now there are a few hardware issues.
First, the cd/dvd drive loads disks, but the system does not recognize anything inserted, and wont play any media. Second, the built in airport card doesnt want to work either, I can see the icon for wireless at the top right of the screen and it lets me plug in my network name and security, but wont connect or see any wireless networks at all, however, ethernet works fine, and it is how I am able to get online now. Lastly, the screen is slightly shifted to the right and the far right of the screen wraps around to the left side of the screen, its not major, probably a 1/4 of an inch, but it is annoying. 

I am sure these are likely driver issues, but when I go to Administration, and Hardware Drivers it does not say I need any drivers. and when I run through "system testing" it says that this version of ubuntu is not genuine, or something like that, but I just burned the install disk last night from ubuntu's website.

Any advice or info would very greatly be appreciated. 
Thanks!

---

### Post by Sef on 2010-02-20
Moved to Apple Users forum.

---

### Post by linuxopjemac on 2010-02-21
The automount of cd's is a bug. [http://ubuntuforums.org/showthread.php?t=1323153&highlight=cdrom](http://ubuntuforums.org/showthread.php?t=1323153&highlight=cdrom)

shift of the screen:
[http://mac.linux.be/content/g5-imac-widescreen-shift-right](http://mac.linux.be/content/g5-imac-widescreen-shift-right)

for wireless you might want to try wicd instead of the network manager.
```
sudo apt-get install wicd
```

---

