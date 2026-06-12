---
title: "Can't install onto G4 PowerMac (AGP)"
date: 2006-08-17
forum: Apple PPC Users
---

### Post by Tofu on 2006-08-17
[CENTER][IMG]http://upload.wikimedia.org/wikipedia/commons/2/2e/Power_Macintosh_G4_Graphite.jpg[/IMG][/CENTER]

Hi there,

I've been trying to install Ubuntu 6.06.1 onto a [G4 PowerMac (AGP) 350MHz]("http://support.apple.com/specs/powermac/Power_Mac_G4_AGP.html"), but without any success.

I start loading the CD, and it gets through the initial boot text OK. Then it seems to start loading the OS. I see the colored Ubuntu logo, and underneath that there is text about loading drivers.

About a minute later it fails. It prints these errors on screen:


```
218.780056] Buffer I/O error on device HDC, logical block 95035
236.255844] Buffer I/O error on device HDC, logical block 95020
233.744857] Buffer I/O error on device HDC, logical block 95021
233.745240] VFS: brelse: Trying to free free buffer
233.745499] Badness in __brelse at fs/buffer.c:1279
233.746114] SQUASHFS error: sb_bread failed reading block 0x2e3c0
233.746339] SQUASHFS error: Unable to read page, block b8eaf5f, size 53a9
241.218323] Buffer I/O error on device HDC, logical block 95020
248.633365] Buffer I/O error on device HDC, logical block 95021
256.108065] Buffer I/O error on device HDC, logical block 95020
263.594171] Buffer I/O error on device HDC, logical block 95021
```

Does anyone have any idea what this could be? A bug, maybe? Is there anything I can do?

Thanks  :)

---

### Post by _jB on 2006-08-17
Almost looks like the error my amd's/g3 ppc give me when "installing" 6.06. 
So for the time being I'm still running 5.10 (on amd's) and debian on my ppc ;)

Have you triede with anything else (5.10, 6.10, debian) yet ?

---

### Post by didg on 2006-08-17
Bad CD or bad CD drive? After all it's a 6 years old box.

---

### Post by Tofu on 2006-08-17
Thanks for the replies. I've found the problem.

As it turns out, the CD disk was OK.  However, as 'didj' suggested, the CD player was not.

The original CD player worked fine in Mac OS X, but failed when installing Ubuntu. I installed a new CD/DVD drive, and now the Ubuntu installation works.

There must be an issue with Ubuntu and some older CD players in 6 year old Macs.

Thanks again, I'm happy that it now works.  :)

---

### Post by RJGill84 on 2006-08-18
WOW - same problem I am having, on the exact same machine. Here is my thread [http://www.ubuntuforums.org/showthread.php?t=237964](http://www.ubuntuforums.org/showthread.php?t=237964) .

Ubuntu CD loads just fine on my G4 laptop, but on my PowerMac G4 (AGP Graphics) it just spits the CD out, without even attempting the boot. The CD is fine, and the drive works fine in OS X. Exact same situation as you. I can't believe replacing the CD drive fixed this...makes no sense that the drive works when the machine is in OS X but not otherwise. So weird. I will try a new drive.

---

### Post by RJGill84 on 2006-08-18
DAMN - wasted alot of time putting a new drive in here for zero results yet again. Very discouraging. The machine just ejects the drive within seconds of POST.

---

### Post by didg on 2006-08-18
Two bad drives in a row? May be or it could be a problem with the open firmware version.

I also have an old G4 and ... it doesn't boot, same stuff, it ejects the CD but I know the drive is bad. I solved it by using a second G4 and moving the HD.

Did you fully test the CD with OSX from the G4 by computing the checksum or copying it? If it works it's likely a pb with OF.

There's small rescue CDs for ppc, you can boot from an USB key and again check the whole CD with md5sum, from linux this time. Again if it works it's likely OF.

You can try to upgrade OF but it's always scary with these old boxes.

Maybe the ISO works from an USB key.

You said you have a second Mac, if you know what you are doing you can try:

- a network install, it works but you have to setup a tftp server.

I Haven't do it but:

- installing in target disk mode via firewire. Dangerous though,could screw you laptop and after that you have to fix manually few things, video and yaboot mainly.

---

### Post by anders_gud on 2006-08-18
> **Tofu said:**
> 

```
218.780056] Buffer I/O error on device HDC, logical block 95035
236.255844] Buffer I/O error on device HDC, logical block 95020
233.744857] Buffer I/O error on device HDC, logical block 95021
233.745240] VFS: brelse: Trying to free free buffer
233.745499] Badness in __brelse at fs/buffer.c:1279
233.746114] SQUASHFS error: sb_bread failed reading block 0x2e3c0
233.746339] SQUASHFS error: Unable to read page, block b8eaf5f, size 53a9
241.218323] Buffer I/O error on device HDC, logical block 95020
248.633365] Buffer I/O error on device HDC, logical block 95021
256.108065] Buffer I/O error on device HDC, logical block 95020
263.594171] Buffer I/O error on device HDC, logical block 95021
```


I have the same problem running the Dapper live CD on a number of machines (with different drives), this must be a bug in the driver... 
Any clues?

---

### Post by avtolle on 2006-08-18
This may be something that you have tried anders_gud, but...instead of the Desktop CD, try downloading the Alternate Install CD for 6.06.1 ppc. That is, if you are wanting to install, IF you are using the Desktop (Live) CD to "see if it works", then are you using the 6.06 LTS or the "new" 6.06.1 LTS Desktop? The latter has the updated kernel, which, for several posters, has allowed the installation of Dapper where the original kernel just wouldn't work. HTH.

---

### Post by Tofu on 2006-08-19
Ubuntu cannot read some older optical drives.

I found this quote from an archived thread:
[QUOTE=warp99]Problem is that most of the older drives were produced before ISO yellow book CDR was available, so some burns will work while others will not. :([/QUOTE]
Link to older thread:
[http://www.ubuntuforums.org/archive/index.php/t-201086.html]("http://www.ubuntuforums.org/archive/index.php/t-201086.html")

---

### Post by wj18 on 2007-08-07
I have the exact same problem trying to install feisty 7.04 onto my System76.. I hope it's not a CD Drive problem.  I'm going to burn another copy of the iso and see if that fixes it.

---

