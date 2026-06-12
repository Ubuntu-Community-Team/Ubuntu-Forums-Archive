---
title: "Problems installing Studio"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by clinto on 2007-06-28
This is a bit odd. I've installed Ubuntu Studio Feisty on my desktop and everything went fine... for the most part. I tried installing it on my neighbor's laptop and it tells me the processor is overheating and it shuts down.

The laptop is an HP Pavilion DV8000. The only changes I've made to the BIOS was the SATA Native Support(for some reason, Windows wouldn't read the hard drives with it turned on). It has two 75GB SATA hard drives. I've left the first one for Windows and I'd installed Ubuntu Feisty on the second one, without any problems.

When I start the Ubuntu Studio live dvd, it loads the menu fine. I select to install, it loads the kernel and the initrd.gz, then it tells me it has failed to allocate mem resource(something it has done ever since I started messing with it, I need to look into this further), then after several seconds, it says critical temperature has been reached (0 C), shutting down, system halted, .

Has this happened to anyone else? If anyone can shed some light as to why it's doing this, I would appreciate it. It happens even when I run the disk check.

---

### Post by jfinkels on 2007-06-29
> **clinto said:**
> This is a bit odd. I've installed Ubuntu Studio Feisty on my desktop and everything went fine... for the most part. I tried installing it on my neighbor's laptop and it tells me the processor is overheating and it shuts down.

The laptop is an HP Pavilion DV8000. The only changes I've made to the BIOS was the SATA Native Support(for some reason, Windows wouldn't read the hard drives with it turned on). It has two 75GB SATA hard drives. I've left the first one for Windows and I'd installed Ubuntu Feisty on the second one, without any problems.

When I start the Ubuntu Studio live dvd, it loads the menu fine. I select to install, it loads the kernel and the initrd.gz, then it tells me it has failed to allocate mem resource(something it has done ever since I started messing with it, I need to look into this further), then after several seconds, it says critical temperature has been reached (0 C), shutting down, system halted, .

Has this happened to anyone else? If anyone can shed some light as to why it's doing this, I would appreciate it. It happens even when I run the disk check.

Open up the back and double check to make sure the heat sink and/or fan are connected properly.

Since when is 0 degrees C critical temperature??? :P

---

