---
title: "Another &quot;Error 13: ~&quot; problem..."
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by WebJoel on 2008-02-22
I have read several "Error 13: Invalid or Unsupported Executable Format" threads and so far, nothing has helped.

 My stats:

 Dual-boot, WIN-XP is master (on C: drive) and Ubuntu (Gutsy) is on the slave/secondary HDD.

 Nothing was done differently or abnormally the last time I used XP, but the next day upon trying to boot I chose to start Window XP, and get the error message:

"Error 13: Invalid or Unsupported Executable Format"

 I tried re-booting several times and tried 'tapping on the F8 key during start-up' to hopefully get into Windows' "SAFE MODE", but cannot get beyond the "Error 13: Invalid or Unsupported Executable Format" message. Clearly, it's in GRUB(??)

 I can use Ubuntu on the secondary drive just fine, of course.

 So, from Terminal, I tried typing:

 sudo gedit /boot/grub/menu.1st

and edit that file to read:

title                Windows XP
root               (hd0,0)
savedefault     
makeactive
map               (hd0) (hd1)
map               (hd1) (hd0)
chainloader    +1

 and SAVE the file, re-boot, and still no change from the "Error 13: ~" message.

 What is wrong here? I rather desperately need to get my XP-drive back. I have NOT edited any files on XP (such as boot.ini, etc..) No re-naming of drives or folders, etc.

 Can anyone assist me?

 Regards,
 -Joel

---

### Post by dca on 2008-02-22
Is it similar to this?
 
[http://ubuntuforums.org/showthread.php?t=277116](http://ubuntuforums.org/showthread.php?t=277116)

---

### Post by Duck2006 on 2008-02-22
> **WebJoel said:**
> I have read several "Error 13: Invalid or Unsupported Executable Format" threads and so far, nothing has helped.

 My stats:

 Dual-boot, WIN-XP is master (on C: drive) and Ubuntu (Gutsy) is on the slave/secondary HDD.

 Nothing was done differently or abnormally the last time I used XP, but the next day upon trying to boot I chose to start Window XP, and get the error message:

"Error 13: Invalid or Unsupported Executable Format"

 I tried re-booting several times and tried 'tapping on the F8 key during start-up' to hopefully get into Windows' "SAFE MODE", but cannot get beyond the "Error 13: Invalid or Unsupported Executable Format" message. Clearly, it's in GRUB(??)

 I can use Ubuntu on the secondary drive just fine, of course.

 So, from Terminal, I tried typing:

 sudo gedit /boot/grub/menu.1st

and edit that file to read:

title                Windows XP
root               (hd0,0)
savedefault     
makeactive
map               (hd0) (hd1)
map               (hd1) (hd0)
chainloader    +1

 and SAVE the file, re-boot, and still no change from the "Error 13: ~" message.

 What is wrong here? I rather desperately need to get my XP-drive back. I have NOT edited any files on XP (such as boot.ini, etc..) No re-naming of drives or folders, etc.

 Can anyone assist me?

 Regards,
 -Joel

The map lines shouldn't be there so edit and remove them so your windoze looks like this

title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

then in the terminal post the output of

sudo fdisk -l

---

### Post by dstew on 2008-02-22
> Clearly, it's in GRUB(??)I don't think so. This error means that grub found a file to load, but it was not an executable file. This can happen if something has changed in your Windows partition, so that now chainload +1 tries to load a text file, for example.

One  way to try to fix this is use the Windows CD, Recovery Console, and the command **fixboot** if you think something may have happened to the XP partition.
EDIT: Also, your command sudo gedit /boot/grub/menu.1st should have been sudo gedit /boot/grub/menu.lst (small 'L'). The first command will indeed create a text file with that name, but that is not the same as the menu.lst file.

---

### Post by WebJoel on 2008-02-22
> The map lines shouldn't be there so edit and remove them so your windoze looks like this

title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

then in the terminal post the output of

sudo fdisk -l I'll do it, and post back. Thanks.

(back) :

 Okay, -here is the sudo fdisk -1 output:

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb909b909

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b7a4f18

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2373    19061091   83  Linux
/dev/hdb2            2374        2482      875542+   5  Extended
/dev/hdb5            2374        2482      875511   82  Linux swap / Solaris
joel@joel-desktop:~$


---

### Post by WebJoel on 2008-02-22
Well, no joy yet. Still getting the "Error 13: ~ . Press any key to continue " message.

  I guess the thing to do next is use the WINDOWS-XP install disk and Recovery, etc. 
 -Can I even get this to load, insomuch the current problems? I've never had to do this before.. I image though since my boot-order places the hard-drive *last*, that the CD-disk will load and I can proceed with this. -Is this correct?

 (Pretty sure that at any point now I am going to mess-up my drives and lose data...) :mad:

 -Joel

---

### Post by Duck2006 on 2008-02-22
Try as dstew posted and reinstall grub again and see if that fixes it.

---

### Post by WebJoel on 2008-02-22
Maybe I can at least VIEW the files on my Master drive, from Ubuntu (on the slave drive). I can't seem to FIND how to do that. :(  I have done it before, -even imported folders and images previously, but I can't see any way to view across HDDs now... What am I missing here?  Is my C:drive 'gone'?? :confused:

---

### Post by Duck2006 on 2008-02-22
Is this what you are looking for?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by WebJoel on 2008-02-22
> **Duck2006 said:**
> Is this what you are looking for?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) >sigh<... possibly, yes. You know, -this would not *be so bad* if I knew what caused this... :confused:  was this caused by Ubuntu, or by something on the XP-side? I haven't used Ubuntu-on-the-E-drive in several weeks (needed some proprietary stuff on XP-side for some client work), and it was last evening when turning on the computer, -Windows would not boot. Fortunately, -I have Linux on E, bootable by default... but I need to access XP *at least* to rescue my files.

 -Still getting "Error 13: Invalid or Unsupported Executable Format
 Press any key to continue" and doing so, takes me back to GRUB and choices (all to boot Linux on E)...

 Looks as if I might have to re-create mount points, eh?

 At any rate, here is this:

 "Places" -"Computer" shows "CD-RW Drive" and "filesystem"

 Clicking "filesystem" shows many folders, and clicking on "Media" shows:

"cdrom" and "cdrom0"

 I thought that there used to be a pair of hard-disks listed here... my ("E") 40GB and my master ("C:") 80GB ... Now, -not there. :(

---

### Post by dstew on 2008-02-23
Did you try **fixboot**?

To look into your NTFS partition (which is /dev/hda1, according to your fdisk output), you need to mount it to your Ubuntu file system. If this happened automatically in the past, then your /etc/fstab file should have an entry in it. We can probably edit this to get it to mount again, assuming the file system on /dev/hda1 is intact. So, post the output of the command```
cat /etc/fstab
```

It is possible that the file system on /dev/hda1 has become corrupted somehow. The best way to check for that is to use the **chkdsk** utility on the WIndows CD, recovery console.

---

### Post by WebJoel on 2008-02-24
> **Duck2006 said:**
> Try as dstew posted and reinstall grub again and see if that fixes it. Probably a great idea, -but "reinstall GRUB" unfortunately doesn't tell me what to do to acheive this. :? I *did* re-install the distro from my CD (wiping everything in the process of course), and downloaded some 190 packages and got Ubuntu back to nearly 90% of what I had before... sans the background-image and several folders/files that I had previously imported from the C: drive (from XP's desktop).

 Still, no indication of multiple drives, so, same result. 

 On another forum it was suggested that I 'unhook the E-drive, let the C-drive be the only one to launch'... This sounded a bit lame but I instead re-started while holding-down the DEL key, got into C-MOS and changed the boot-order to boot "hd0" first, -same thing (right?).

 Anyway, I shut down and using the XP installation disk, booted and pressed "R" for "restore". Was not sure what expect there, -all DOS-looking stuff, but did "CHKDSK" and it returned a "Unrecoverable error found" among other things (indication OK).
 I re-ran CHKDSK and this time, -**no** "unrecoverable errors found" return.. (??)

 I did a few more things, -re-set (I forget now what it was, 
"MBR"-maybe?? but it indicated to _not do this IF you CAN_ get into the C:-drive, -which I could NOT...), -nothing seemed 'repaired', so shut down and let the computer re-boot, ...and it booted cleanly into XP so maybe, -just maybe, -this fixed something... Or maybe having hd0 boot first(?). I want my E-drive (hd1) to boot first and have GRUB let me chose to proceed, or scroll-down and select XP-HOME on C:

 I am missing the dual-boot, -missing Ubuntu Linux, but I think I'll let this set as-is for awhile before I do anything else... :lolflag:

---

### Post by WebJoel on 2008-02-24
> **dstew said:**
> Did you try **fixboot**?.... ....It is possible that the file system on /dev/hda1 has become corrupted somehow. The best way to check for that is to use the **chkdsk** utility on the WIndows CD, recovery console. No, -did not try "fixboot". Is this on GRUM, or XP?

 I *did* (as you can see from my previous post), use the XP disk and "R" when booting from CD, and maybe I got lucky and fixed something.

 Next goal is to get dual-boot back, as XP refuses to acknowledge that there is another OS on another HDD...

---

### Post by Duck2006 on 2008-02-24
Have a look through this page it may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ajsemple on 2008-03-09
I had the same problem and found the solution as follows.

Open menu.lst and chack to see if the following entry is at the bottom of the file

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd5
title		Microsoft Windows XP Professional
root		(hd2,4)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

This entry had be added I presume by some update.

I deleted this entry and everthing works as usual.

I have presumed that XP is on your main drive and that Ubuntu on a different partition or hard drive.

CX500UK

---

