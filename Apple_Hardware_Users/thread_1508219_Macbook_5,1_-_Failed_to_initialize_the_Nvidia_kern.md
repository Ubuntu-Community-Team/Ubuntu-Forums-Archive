---
title: "Macbook 5,1 - Failed to initialize the Nvidia kernel module"
date: 2010-06-12
forum: Apple Hardware Users
---

### Post by ace55 on 2010-06-12
Hello all,

This problem has bothered me in both my previous install of 10.04 and my current one. Intermittently, booting into ubuntu results in ubuntu running in low-graphics mode, informing me that the Nvidia kernel module has failed to initialize. 

Running nvidia-xconfig does not help. Removing and then reinstalling the nvidia driver in Hardware drivers does not help. I experience the issue with both the 173 and current drivers.

Anyone else experiencing this problem? I love ubuntu, but this is making me seriously consider exploring other distros. Perhaps this not a bad thing - after I return from this exploration, hopefully someone will have a solution for this problem. :)

Thanks in advance.

---

### Post by EchohcE on 2010-06-12
I got this problem after I got fed up with bluetooth and uninstalled it  completely.  I didn't realize that my Airport relied on it, so I had to  use an ethernet connection to reinstall gnome-bluetooth and its related  packages.  Now my bootup hangs on lib_crypt or lib_config(can't remember  which), then it spasms low-graphics (large Ubuntu loading screen) and  goes to the login screen.

It should be said that I use a dual-boot of Leopard and Lucid 64-bit.  I  followed 7-13 of Jamesixgun's post on manually partitioning for  dev/sda3.  His process, which I followed without having to reinstall OSX  or use Bootcamp(I used Disk Utility in OSX to create the free space),  is here:

[http://ubuntuforums.org/showthread.php?t=1297229&page=8](http://ubuntuforums.org/showthread.php?t=1297229&page=8)

---

