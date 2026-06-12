---
title: "MacOnLinux Problems... Worked, now out of memory"
date: 2006-07-18
forum: Apple PPC Users
---

### Post by Ryan Marcus on 2006-07-18
I just installed Ubuntu on my eMac with 1 GB of ram.

I installed MoL from the instructions in the Wiki, and then started it. (startmol --osx), went through the registration process, made an account and logged in. Then I shut down the macintosh, rebooted it, and installed the MoL tools that where on the desktop. I restarted again, but when I tried to run it again I got this:

> 
Mac-on-Linux 0.9.70 [Jul 23 2005 19:20]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Running in PowerPC 7400 mode, 500 MB RAM
Timebase: 33.17 MHz, Bus: 132.71 MHz, Clock: 999 MHz
Using USB mouse on /dev/input/mice
OHCI USB controller registered
Could not open '/var/lib/mol/x11.kbd'
Fullscreen video on VT 8.
Could not open '/var/lib/mol/console.kbd'
Video driver(s): [xvideo] [console_video]

     640* 480, depth 8,32   { 0.0 } Hz
     800* 600, depth 8,32   { 0.0 } Hz
    1024* 768, depth 8,15,32   { 0.0 } Hz
    1152* 864, depth 8,32   { 0.0 } Hz
    1280*1024, depth 8,32   { 0.0 } Hz
    1600*1200, depth 8,32   { 0.0 } Hz

ALSA sound driver (device 'default')
MOL SCSI controller registered


    <No SCSI Devices>

    CD   /dev/cdrom       CD-ROM         <read-only>   ------
----> /dev/hda2 might be a boot-strap partition.
------> /dev/hda3 is linux-mounted with write privileges.
Could not open '/dev/hda3' with read-write permissions
No volumes found in '/dev/hda'
No volumes found in '/dev/hdb'
    Unembedded HFS+ /dev/sda3                       <rw> 73180 MB
No volumes found in '/dev/sdb'


>> ==================================================
>> MacOS X Boot Loader 0.9.70
>> Candidate boot volume: /mol-blk@0/disk@0:0
>> /mol-blk@0/disk@0:0,\mach_kernel (4338660 bytes)
>> Old mkext timestamp (or safe-boot)
>> Loading from /mol-blk@0/disk@0:0,\System\Library\
>> --> Boot loader failure: Out of memory
cleaning up...
Terminating threads...
DONE


I opened up /etc/mol/molrc.osx and changed the memory from 128 to 500, and got the same result.

I then tried 900, which is 100 MB away from what my computer has, and got the same error.

What did I do? :(

Edit: When I watch my memory activity, it never goes above 14%.

---

### Post by BadOp on 2006-07-19
Hi, I had the exact same issue.

The solution is to download Mattias Nissler's modified bootloader from here: [http://www-user.rhrk.uni-kl.de/~nissler/mol/]("http://www-user.rhrk.uni-kl.de/~nissler/mol/") and follow the instructions on that site.  This solution fixed the memory issue for me. Good luck.

---

### Post by Ryan Marcus on 2006-07-19
Thanks, that solved the problem.

---

### Post by stmiller on 2006-08-03
I've got the exact same problem. Using this other guy's bootx image did not fix the problem; it only reported the boot image does not work.

```
Fatal error: drivers/bootx is not an ELF image
```

-----
Edit: Going instead to try to compile the latest mol from the external link from the ubuntu mol-how-to page.

---

