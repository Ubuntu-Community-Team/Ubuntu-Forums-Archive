---
title: "Ubuntu / windows partition"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Mr Whippy on 2006-12-23
Hi - 

Just installed 6.10 yesterday, (first time ever with linux) on my C drive.

The original OS is Win 2K, and the drive is partitioned 50:50 for windows & ubuntu.

When in Ubuntu, I cannot see the windows partition, or even my second physical hard disc where all my mp3's etc. live. CDs/ DVD/s are showing OK though.

Using the Ubuntu help, it says go to System, Administration, Discs, but there is no "discs" option under Adminstration, or anywhere else I can find for that matter. Am I doing something wrong or is the help information incorrect ?

My second question - (sorry if I'm being extremley thick here) but on this help page regarding making windows partitions automatically available - [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html")
it shows what to me seem like command line instructions. How do I get to this "command line" to enter the instructions ?

Any help appreciated (Complete newbie, so please be gentle !)

Cheers - Dave.

---

### Post by LDRoamer on 2006-12-23
To get to a command line go to applications -> accessories -> terminal.  This will open a terminal window and give you a command line. You might want to read up on using "sudo" at the command line as well.

---

### Post by moma on 2006-12-23
Command line.
Start gnome-terminal from Applications -> Accessories -> Terminal menu. You can also press ALT + F2 and run command: gnome-terminal

The instructions you found are OK. 

Read also chapter 1.15  (especially 1.15.3) of this important guide.
[http://easylinux.info/wiki/Ubuntu_Edgy](http://easylinux.info/wiki/Ubuntu_Edgy)
+
Finalize your desktop (steps 5 - 8 ): [http://www.futuredesktop.org/](http://www.futuredesktop.org/)

Merry xmas,

---

### Post by Sef on 2006-12-23
Could you open the terminal and type this:

```
sudo fdisk -l
```

This will show how your hard drive is partitioned.   Could you please copy and paste it here.  Thank you.

---

### Post by Mr Whippy on 2006-12-23
Thanks everyone for the quick replies...

I've got to the command line OK now - thanks. :) 

BUT - 

I have yet to configure ubuntu to connect to my ISP (not even started trying to figure that one out yet), and also my printer isn't working in ubuntu, so I'm having to do everything in windows, reboot to ubuntu and try it, and scribble everything down on bits of paper ! AARRGGH !

**LD roamer **- Thanks, I've sussed that bit out now.
[B]
Moma[/B] -  I've read & printed (in windows) section 1.15, I'll try it out on the next boot to ubuntu.
As for the finalisation thing, I think I'll have to wait till I get my ADSL working in ubuntu first.
Thanks.

**Sef -** This is the result - (via paper scribblings & retyping, so I hope I haven't made a mistake)

Disc /dev/hda: 120gb 120034123776 bytes
255 heads, 63 sectors/track, 14593 cyls
units = cylinders of 16065 * 512 = 8225280 bytes

device        boot   start    end     blocks          id      system 
/dev/hda1   *        1       7153    57456441     7       HPFS/NTFS
/dev/hda2            7154  14310   57488602+   83     LINUX
/dev/hda3           14311 14593   2273197+     5       Extended
/dev/hda5           14311 14593   2273166       82     Linux swap/solaris

Disc/dev/hdc: 122.9 gb, 122942324736 bytes
225 heads, 63 sectors/track, 14946 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes

Device         boot   start    end     blocks           id   system
/dev/hdc/1    *        1      14945  120045681     7    HPFS/NTFS

I'm going to go back to ubuntu and try the command line stuff from section 1.15, but I still don't know why I'm not seeing a "disks" option under the "administration" menu.

Also - does anyone have a quick setup guide for getting online with my ADSL modem onto btinternet ?

Thanks again - Dave.

---

### Post by Mr Whippy on 2006-12-23
Sorry about that, Sef, the forum has taken out all my spacing to make the collums line up !

Hope you can read it OK.

Dave.

---

