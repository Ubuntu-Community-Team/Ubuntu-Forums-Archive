---
title: "915resolution permission problem"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by seamusx on 2006-11-22
I have a problem making 915resolution work. I searched for it on other thread but I didn't find similar problem.

My laptop: 
Acer Aspire 5610  
Chipset Mobile Intel® 945GM 
Ubuntu 6.06 
I installed 915resolution with 
apt-get install 915resolution 
 
and listing my screen rsolution with 915resolution -l 
 
```
Intel 800/900 Series VBIOS Hack : version 0.5.2 
 
Chipset: 945GM 
BIOS: TYPE 1 
Mode Table Offset: $C0000 + $269 
Mode Table Entries: 36 
 
Mode 30 : 640x480, 8 bits/pixel 
Mode 32 : 800x600, 8 bits/pixel 
Mode 34 : 1024x768, 8 bits/pixel 
Mode 38 : 1280x1024, 8 bits/pixel 
Mode 3a : 1600x1200, 8 bits/pixel 
Mode 3c : 1280x800, 8 bits/pixel 
Mode 41 : 640x480, 16 bits/pixel 
Mode 43 : 800x600, 16 bits/pixel 
Mode 45 : 1024x768, 16 bits/pixel 
Mode 49 : 1280x1024, 16 bits/pixel 
Mode 4b : 1600x1200, 16 bits/pixel 
Mode 4d : 1280x800, 16 bits/pixel 
Mode 50 : 640x480, 32 bits/pixel 
Mode 52 : 800x600, 32 bits/pixel 
Mode 54 : 1024x768, 32 bits/pixel 
Mode 58 : 1280x1024, 32 bits/pixel 
Mode 5a : 1600x1200, 32 bits/pixel 
Mode 5c : 1280x800, 32 bits/pixel 
 
```
 
 
I chose unused mode (I tried 50 and 41) to run 
 
```
915resolution 50 1280 800 32: 
 
Intel 800/900 Series VBIOS Hack : version 0.5.2 
 
Chipset: 945GM 
BIOS: TYPE 1 
Mode Table Offset: $C0000 + $269 
Mode Table Entries: 36 
 
Patch mode 50 to resolution 1280x800 complete 
```
 
 
So I reboot my system. 
 
At graphic login panel, all was ok (resolution 1280x800 too) but when I login in my system i saw for just a second console login and then graphic login screen again. 
(username and password was correct) 
 

If I run startx from root, all is ok (X-server starts and gdm too) but not if i run startx from normal user.

This is my log file (with startx 2> file.txt) with normal user.

```
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x86) [0x80b4ab6]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers/i810_drv.so(I830Rotate+0xea3) [0xb79decc2]
3: /usr/lib/xorg/modules/drivers/i810_drv.so [0xb79d083b]
4: /usr/lib/xorg/modules/libramdac.so [0xb77ddb6d]
5: /usr/bin/X11/X [0x80bade8]
6: /usr/bin/X11/X(xf86SwitchMode+0xb8) [0x80b108a]
7: /usr/bin/X11/X [0x80d0287]
8: /usr/bin/X11/X [0x80d0477]
9: /usr/bin/X11/X [0x8144cc5]
10: /usr/bin/X11/X(Dispatch+0x19e) [0x8085d56]
11: /usr/bin/X11/X(main+0x47c) [0x806e0d8]
12: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d7eea2]
13: /usr/bin/X11/X(FontFileCompleteXLFD+0x85) [0x806d641]

Fatal server error:
Caught signal 11.  Server aborting

xinit:  connection to X server lost.
```

Any ideas? 
 
thanks a lot 
Seam

---

### Post by davmac on 2006-11-22
Hi,

Not sure if this is the answer to your problem but the way I got 915resolution to work was to update 915resolution's config file. 

Have a look at this thread [http://www.ubuntuforums.org/showthread.php?t=302869](http://www.ubuntuforums.org/showthread.php?t=302869) and follow from step 5 in the final response.

Hope this helps,

Dave Mac

---

### Post by seamusx on 2006-11-24
hy Dave,
thanks for your reply. 
I already tried your solution, but the problem have persisted.
I think it must be a permission problem, but I don't understand where..:confused: 
If I install 915resolution and run X with startx as root, it starts, but with normal user it doesn't and give me the error....
](*,) 
M

---

### Post by rlozano on 2006-11-24
> **seamusx said:**
> hy Dave,
thanks for your reply. 
I already tried your solution, but the problem have persisted.
I think it must be a permission problem, but I don't understand where..:confused: 
If I install 915resolution and run X with startx as root, it starts, but with normal user it doesn't and give me the error....
](*,) 
M

did you make the configuration as a root or as your regular login uid?

---

### Post by seamusx on 2006-11-28
I Installed 915resolution as root, run 
```
915resolution 50 1280 800 32: 
```
as root
and also change 915resolution configuration file as root.
If I try to do so as normal user
```
915resolution 50 1280 800 32: 
```
it gives me "permission denied"
s

---

