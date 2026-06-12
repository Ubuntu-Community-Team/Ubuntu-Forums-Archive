---
title: "TIP: Update your system with one command"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by elemental666 on 2006-06-13
Tired of continuously typing 3 commands to update your system?  I know I was.  Going through all these howtos and tweaks you do alot sudo aptitude update/upgrade/dist-upgrades.  Well here's how you can do all three all at once:

open your favorit text editor and paste this in:

```
#!/bin/sh
sudo aptitude update
sudo aptitude upgrade
sudo aptitdue dist-upgrade

```

save that to your home directory as sysupdate or something similar, then enter:
```
chmod 755 sysupdate
```

if you called it something other than sysupdate make sure you use your filename instead.
copy it to your /usr/bin
```
sudo cp ~/sysupdate /usr/bin
```

anytime you see the update icon light up, or need to update before tweaking, installing something, from anywhere in the fs, enter:
```
 sysupdate
```

---

### Post by xfile087 on 2006-06-13
Nice tip! Good work!

---

### Post by JSchwage on 2006-06-13
Thanks for the tip. But shouldn't this be in the "HOWTOs, Tips & Tricks" section?

---

### Post by anaconda on 2006-06-13
hmmm...
Does it ask root password 3 times?
I mean sudo..., sudo..., sudo...
How about making it like:

sudo su
aptitude ...
aptitude ...
aptitude ...
exit

the sudo su would make you root until the next exit....

ANd if you copy the resulting file to /bin or /usr/sbin then you could just run it with "sysupdate" from anywhere..

Or you could make /bin folder to your home folder, and add it to the PATH...

---

### Post by Bloch on 2006-06-13
I thought the system was automatically updated once you are online? I get such updates every couple of days

---

### Post by elemental666 on 2006-06-13
It'll only ask for the password the first time, there is a grace period for sudo.

Also that run command has been updated. Thanks Anaconda!

I put it here because I thought that the people viewing it here could use it most.  If it needs to be moved, that's fine by me.

Yes the system will automatically search for updates and let you know, then you have to open the update manager, enter the password, wait for it to refresh, then install, wait for it to refresh, then close.  Much faster to open a term and run this script when you see the update icon light up.

---

### Post by 5-HT on 2006-06-13
[quote=elemental666]Tired of continuously typing 3 commands to update your system?  I know I was.  Going through all these howtos and tweaks you do alot sudo aptitude update/upgrade/dist-upgrades.  Well here's how you can do all three all at once:

open your favorit text editor and paste this in:

```
#!/bin/sh
sudo aptitude update
sudo aptitude upgrade
sudo aptitdue dist-upgrade

```.... [/quote] 

I could very well be wrong here, but wouldn't you need to add either '-y' or '--assume-yes' for Aptitude to automatically answer yes when a yes/no prompt is presented when installing/upgrading/removing packages?

i.e. (with root permissions), 

```

aptitude update && aptitude upgrade -y && aptitude dist-upgrade -y

```

---

### Post by elemental666 on 2006-06-13
no your right, I didn't want to auto answer, I like to see what's being done.  If you want to use that method your more than welcome to.  This was never meant to be comprehensive.  This is a very simple shell script.  Just thought I'd seed the idea of making your own scripts, ya know.  Feel free the alter it, in fact I encourage everyone to do just that.  Make it to your liking and have fun learning on the way!

---

