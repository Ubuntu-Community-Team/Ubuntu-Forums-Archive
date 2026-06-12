---
title: "iMac G3 really slow"
date: 2007-06-19
forum: Apple PPC Users
---

### Post by adwatkin19 on 2007-06-19
I have tried to install Feisty, edgy and then dapper on my Imac G3. But they all run slow. It takes about 30 seconds to register any movement of the mouse, any command etc. 

The live CD's didnt seem to run, but the alternate CD's all worked well. 

The Specs are G3 600mhz, 256mb ram 40GB hdd.

I also tried putting os x back on to get it back running again, but the installer couldnt see the hdd for some reason only the installation disc. any ideas on this?

thanks for any help and advice

adwatkin19

---

### Post by 3rdalbum on 2007-06-19
Open the file /etc/X11/xorg.conf:

```
sudo nano /etc/X11/xorg.conf
```

Now make sure that under Section "Module", you do not have this line:

```
Load "dri"
```

If it is there, delete it. Press Control-X, then the Y key, then Return to save changes to the file. At the command-line, type:

```
sync
```

Then press Control-Option-Delete to kill the X server. When the X server starts up again, hopefully things should be running at the correct speed.

If that doesn't help, and nobody has any way to help you, then you can reinstall OS X. You must use the Drive Setup program on the OS X disc to initialise the hard disk into HFS+ format, then the installer will be able to see the disk.

---

