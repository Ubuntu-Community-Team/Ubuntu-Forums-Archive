---
title: "i just made a bootable USB and i am getting a error at boot"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by sam1981 on 2008-02-15
could not find kernel image: vmlinuz

---

### Post by mrsteveman1 on 2008-02-16
Which guide are you following (if any)?

Sounds like a syslinux error, it means that the syslinux.cfg file is either missing or not in the right place, or perhaps doesn't point to the kernel in the correct place.

---

### Post by Akovia on 2008-02-19
Almost same problem here, except I don't get an error. It boots to a menu that looks identical to the Live-CD and if I click on any of the choices it pops up a little window with the following text "Boot Loader" , "VMLINUZ" and an "OK" button. Clicking OK does nothing.

Following this guide: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

The directions were pretty good, and only ran into a few troubles.

1. Using printed instructions, I ran into a couple instances where I missed putting in a "space" character where it needed one. The commands failed without incident and didn't run luckily and was able to find my mistakes.
2. The guide "Essentials" lists U710fix.tar as the file needed but the command refers to U710fix.zip. No big deal except the command listed for U710fix.zip fails.

```
19. Type wget pendrivelinux.com/downloads/U710fix.zip
```

It took me a while to figure out but the command didn't start with http://

```
19. Type wget  http://pendrivelinux.com/downloads/U710fix.zip
```

Except for those minor hurdles, everything went smooth. I checked the files in U710fix.zip (isolinux.txt,syslinux.cfg) against what was on my USB and they match. 

I would be happy to report any requested info if it would help to fix this. I wanted to post to the article itself but didn't find any forums or places for feedback.

Thanks,
Akovia

---

### Post by Akovia on 2008-02-19
I am writing this from my pendrive installation. I think I fixed the problem, just hope I did it right.

Comparing isolinux.txt against syslinux.txt from the U710fix.txt, I noticed that the pointer to the Kernel was different.

isolinux.txt
```
KERNEL  casper/vmlinuz
```

syslinux.txt
```
KERNEL  vmlinuz
```

I changed syslinux.txt to point to casper directory instead of copying the vmlinuz to the root directory. I also changed the the first line to point to the first menu item instead of the Kernel.

old syslinux.txt
```
DEFAULT  vmlinuz
```

changed to
```
DEFAULT  persistent
```

It works, but I am worried since I don't know which way it was supposed to happen. I do know that constant writing to USB drives is bad, and not sure if the problem was that vmlinuz was in the wrong directory, or if the syslinux.txt was wrong and how it will effect the life of my pendrive. Could someone in the know chime in on this?

In any case, as I posted before, my installation went very smooth for a newb like me and hand typing in that many commands so it seems to me that anyone following the same guide will end up with the same results. If so, this fix should get you going unless someone chimes in that this is a bad fix. If that happens, please believe them instead. :)

Cheers,
Akovia

---

### Post by mrsteveman1 on 2008-02-19
If the kernel fails to load (IE it just tells you "linux" not found), thats a syslinux error because it couldn't find the config file, IE syslinux has no idea what the kernel is actually called so it tries to load one named linux first.

If it tells you vmlinuz wasn't found, thats because syslinux read the config file, saw the kernel was named vmlinux/vmlinuz, but couldn't find it where the config said it would be. 

Writing to USB drives isn't a real problem, theoretically if you wrote to a single sector 10,000 times it would fail, but that isn't going to happen. With wear leveling on the controller chip (inside the stick), it's difficult to get a USB flash stick to fail early or at all. If you were writing data to it randomly, perhaps it would be different, but the device is only written to when filesystem changes take place since most of root is a read only squashfs filesystem.

---

### Post by Akovia on 2008-02-20
Thanks for the reply steve. It turns out that I have more problems to sort out and don't want to hijack this thread any longer. After doing more research it does seem that there should be a copy of vmlinuz in the root directory so I would reccomend anyone else with the same trouble find out why the Kernel is missing from the root of the USB drive and not to try and fix it by pointing to the Kernel in the casper directory. 

I can't yet say if my new problems are the result of this or not but I started a new thread to try and find out. [http://ubuntuforums.org/showthread.php?p=4369244#post4369244](http://ubuntuforums.org/showthread.php?p=4369244#post4369244)

Thanks again steve for the insight on long term writing stability on usb drives. 

Regards,
Akovia

---

