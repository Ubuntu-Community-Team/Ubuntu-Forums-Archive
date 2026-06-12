---
title: "iBook G3 issues w/ OS 9.2 and Ubuntu 8.04"
date: 2009-04-28
forum: Apple Hardware Users
---

### Post by Can-of-Bees on 2009-04-28
All - 

Thanks for reading and any assistance you can give.

In the process of trying to trouble-shoot a faulty network port on an OS 9.2.2 iBook (G3, 500mHz), and becoming frustrated with OS 9, I thought I'd try looking at things from a *nix perspective (using an Ubuntu 8.04.1 Live CD) where I'm a little more comfortable.

Well, I seem to have really screwed something up, because, while the iBook would boot from the Live CD, now it doesn't want to boot at all - from the HD or from the CD. It seems like it's running through mud - I've had a "Please wait, loading kernel..." message on the screen for at least 30 minutes.

A search didn't turn anything up here on this forum, and I haven't had any luck finding anything on the Web.

Any advice? Any suggestions?

Thanks very much!
C-o-B

---

### Post by mclarenracer on 2009-04-28
Will it even turn on? Check the obvious, it has charge in its batteries, etc. Hopefully you have your mac os x install dics? If you do then pop those in and see if you can get it to boot that way. Unfortunately you would have to reinstall ubuntu.

---

### Post by Can-of-Bees on 2009-04-28
> **mclarenracer said:**
> Will it even turn on? Check the obvious, it has charge in its batteries, etc. Hopefully you have your mac os x install dics? If you do then pop those in and see if you can get it to boot that way. Unfortunately you would have to reinstall ubuntu.

The battery has a charge and the AC adapter is plugged in and working, too.

It'll boot to a gray screen, pause for several minutes, and then flash to an Apple-Face/question mark screen. Almost the same problem with trying to boot from the Ubuntu Live CD - it makes it to the live prompt, then starts loading the kernel and then freezes.

I think I might try a re-install of the Mac OS.

---

### Post by tiresia on 2009-04-29
Can you please post more info about your mac (RAM...)
If you want just to install Ubuntu, it would be easier and lighter for your computer to start from an alternate CD.
If you want a LiveCD, I would go with the new Xubuntu 9.04
Download it here [http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/)
or serch for the .torrent file here [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

Are you sure you downloaded the right powerpc CD? And burn it (with the Apple Disk Utility if you have MacOSX) at low speed.

---

### Post by Can-of-Bees on 2009-04-30
Tiresia - 
hi. There's been a little progress, however I hit another stumbling block.

I'm using an Ubuntu 8.04.1 Alternate Install CD. The iBook is a 500mHz PowerPC, dual USB, 384MB RAM. 

I've been able to get part way into the install process when the installer decides that it cannot recognize the CD-ROM drive. I've ALT+F2'd to the shell, ls /dev, but I'm unable to determine which /dev is the CD-ROM.

Thanks for your suggestions.
C-o-B

EDIT: all, my apologies. I just discovered a thread covering this exact issue. thanks.

---

### Post by tiresia on 2009-04-30
> **Can-of-Bees said:**
> 
I've been able to get part way into the install process when the installer decides that it cannot recognize the CD-ROM drive. 
I've read your post also in the other thread. You shouldn't have such a problem with detecting the CD-ROM with the Ubuntu Hardy Installer.
Can you please tell us, when do you get such a message?
Or could you please try to boot with another CD, maybe with jaunty?

---

### Post by Can-of-Bees on 2009-04-30
Tiresia -- 
thanks for the response.
> Can you please tell us, when do you get such a message?
I get 'no common CD-ROM' message after the keyboard selection process. After trying the modprobe fix, I was stuck in a loop (Step 3 - CD-ROM, attempting the fix process, failure, and then returning to Step 3). 
> Or could you please try to boot with another CD, maybe with jaunty?
I'm burning an ISO of Jaunty as I type.

Thanks again for your help.
C-o-B

---

### Post by Can-of-Bees on 2009-04-30
I've experienced this same error with Ubuntu 8.04.1 (and Xubuntu 8.04) alternate install cds -- this is the error from Jaunty 9.04 alternate:

/pci@f2000000/mca-io@17/ata-4@1f000/disk@1:2,\install\yaboot.conf: Unknown or corrupt filesystem.

The Jaunty alternate downloaded and burned without errors - I can try a second download.

Thanks!

---

### Post by tiresia on 2009-04-30
> **Can-of-Bees said:**
> I've experienced this same error with Ubuntu 8.04.1 (and Xubuntu 8.04) alternate install cds -- this is the error from Jaunty 9.04 alternate:

/pci@f2000000/mca-io@17/ata-4@1f000/disk@1:2,\install\yaboot.conf: Unknown or corrupt filesystem.

The Jaunty alternate downloaded and burned without errors - I can try a second download.

Thanks!
I'm afraid that is not related to a corrupted file. Is the CD-ROM the original one?

---

### Post by Can-of-Bees on 2009-04-30
> **tiresia said:**
> I'm afraid that is not related to a corrupted file. Is the CD-ROM the original one?

I couldn't say. I think it is, but I'm not sure; it's a tray-loading CD-ROM, which seems to match this model.

I could be wrong, tho.

What's weird about this is the fact that the above error message doesn't happen every time. Earlier I wasn't getting this error message (with the same alternate install disks). Very confusing.

---

### Post by tiresia on 2009-04-30
Please, try again booting from the Jaunty installer after resetting PRAM holding down the keys ctrl-alt-P-R at boot up (the computer will restart)

If it does not work, boot again in Open Firmware, holding down ctrl-alt-O-F
At the prompt type ```
devalias
```
OpenFirmware will list the alias for your devices. Look for the alias 'cd'
Is the path the same that you get when yaboot fails to boot?
Try then following
```
boot cd:,\install\yaboot 
```

---

### Post by Can-of-Bees on 2009-04-30
> **tiresia said:**
> ```
boot cd:,\install\yaboot 
```

The devalias for cd matches the error code. When I tried your boot suggestion, I get the following error message:

```
DISK-LABEL: read of block0 failed
ATAPI-DISK: open of DISK-LABEL failedCan't open device </pci@f2000000/mac-io@17/ata-4@1f000/disk@1:0>
```

This seems to imply that there's something wrong with the CD-ROM, but again - sometimes it works and sometimes it gives me this ( which is probably the strongest indication that something is wrong. :) )

Thanks again.

---

### Post by tiresia on 2009-04-30
Well, actually it looks like the OpenFirmware path for cd is  '-/disk@1:0', but pressing C at boot the kernel message says that the corrupted file system is on '-/disk@1:2'
Can you please check better for similar names for cd with devalias?

---

### Post by Can-of-Bees on 2009-04-30
> **tiresia said:**
> Well, actually it looks like the OpenFirmware path for cd is  '-/disk@1:0', but pressing C at boot the kernel message says that the corrupted file system is on '-/disk@1:2'
Can you please check better for similar names for cd with devalias?

Sorry - you're right:
```
0 > devalias cd /pci@f2000000/mac-io@17/ata-4@1f000/disk@1 ok
```

I don't know how else to check for other names for cd with devalias - I'm leaving work and will investigate from home.

Thanks again for your help.

---

### Post by tiresia on 2009-04-30
I meant just, that you should read if you have a similare name (alias) like cd or ata1 etc.
Anyway if you don't want to bother with openfirmware, you can try to install from a usb stick Here a link [https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld) (read the section Booting from USB memory stick)

---

