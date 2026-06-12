---
title: "Ubuntu system broken"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by rayp on 2007-08-16
Hi,

I have had a Ubuntu 6.06 server installed and running for about a year and suddenly it will not boot up.  Grub returns an 'Error 15: File not found' when trying to load the kernel.

I have used aptitude regularly to update the system and ran an update yesterday.  Today I cannot boot.

I am quite new to Ubuntu and I don't really know what to do next.  I haven't moved the kernel files.

Can anyone give me a pointer, even if it is that I have posted this in the wrong forum :-)

Thanks,

Ray

---

### Post by chrisN_uk on 2007-08-16
Not sure I can help much, any idea where the problem is? Some error logs might help. Can you post /var/log/boot and /var/log/Xorg.0.log?

---

### Post by hyper_ch on 2007-08-16
If you haven't changed anything then I would tend to think it's a harddisk/partition problem... Have you got a Desktop-CD? If so, boot linux from there and then have your partitions checked... maybe that helps.

---

### Post by rayp on 2007-08-16
> **chrisN_uk said:**
> Not sure I can help much, any idea where the problem is? Some error logs might help. Can you post /var/log/boot and /var/log/Xorg.0.log?

Thanks for the reply.

I have used the server CD 'repair broken system' option to run a shell on the drive so I can see what is on the drive.  The kernel images seem to be where Grub is looking for them in the /boot directory.

However the logs you mention are not in /var/log.  It's a bit difficult for me to post anything anyway because, although the machine is connected to the network, I don't know how to access it remotely when it is not properly booted.

Ray

---

### Post by rayp on 2007-08-16
> **hyper_ch said:**
> If you haven't changed anything then I would tend to think it's a harddisk/partition problem... Have you got a Desktop-CD? If so, boot linux from there and then have your partitions checked... maybe that helps.

Yes I have a desktop CD.  How do I check the partitions once it is loaded?

Ray

---

### Post by rayp on 2007-08-17
> **hyper_ch said:**
> If you haven't changed anything then I would tend to think it's a harddisk/partition problem... Have you got a Desktop-CD? If so, boot linux from there and then have your partitions checked... maybe that helps.

OK, I loaded the Desktop-CD.  First I tried looking at the hard drive using the Disks Manager.  It showed /dev/hda1 as Inaccessible.  When I clicked Enable it did not change anything.

Then I tried to browse to the hard drive using the File Browser.  It showed hda with the same icon as it used for the CD ROM drive, suggesting that it thinks it is a removable drive.  Sure enough, double clicking the icon gave an error message - 

Unable to mount the selected volume.

error: device /dev/hda1 is not removable
error: could not execute pmount

So I then tried manually mounting hda1 from a terminal.  That worked fine and I can access the files on hda1 using the Filesystem icon in the File Browser.  Everything seems okay as far as I can see.

Next I ran fsck -f on hda1.  It did not report any problems.

Now I am a bit stuck.  Everything seems okay.  My data seems to be intact on hda1 but the system will not boot to it.  The only inconsistency I have seen is the fact that Ubuntu seems to think that hda1 is a removable disk and maybe uses the wrong method of mounting it?

Any idea what I can do next?

Many thanks,

Ray

---

### Post by Sef on 2007-08-17
This  is GRUB error 15:

> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.


Have you tried reinstalling [GRUB]("http://doc.gwos.org/index.php/Restore_Grub")?

---

### Post by aquavitae on 2007-08-17
It could be a problem with a new kernel.  If you've had it for a year chances are its done a few kernel upgrades.  In grub, do you have anumber of ubuntu kernel options, e.g. 2.6.16, 2.6.17, 2.6.18?  If you do, try an older one and see if it gets anywhere.  Can you boot into recovery mode?
> The kernel images seem to be where Grub is looking for them in the /boot directoryI assume you mean you've checked the file names against whats in menu.lst?

---

### Post by ramjet_1953 on 2007-08-17
Super GRUB disk is good for any sort of GRUB issue.

It is an iso that you burn to a CD.

You just boot from the CD and you can recover your GRUB install

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Regards,
Roger 8)

---

### Post by rayp on 2007-08-17
> **Sef said:**
> This  is GRUB error 15:




Have you tried reinstalling [GRUB]("http://doc.gwos.org/index.php/Restore_Grub")?


Yes I have.  I tried it with the original menu.lst in place and it made no difference.  I then noticed that, although the Desktop-CD was reporting the drive as hda1 menu.lst was showing...

root (hd1,0)
kernel /boot/vmlinuz-2.6.15-28-server root=/dev/hdb1 ro quiet splash

so I changed it to

root (hd0,1)
kernel /boot/vmlinuz-2.6.15-28-server root=/dev/hda1 ro quiet splash

and the boot up error has now changed to...

Error 17: Cannot mount selected partition


It seems to me that, for some reason, the BIOS is changing the hard drive allocations so grub cannot mount the correct partition and so cannot find the kernel.  Could this be what is happening?

I should perhaps mention that I did edit menu.lst a few months ago when I installed 2 extra hard drives as a RAID mirror pair.  That caused almost the same problem but the reason was obvious then as I had installed new drives and moved the bootable drive.  That's why menu.lst had hdb1 etc it it.  I don't understand why the system suddenly cannot find the boot drive now though.

Thanks,

Ray

---

### Post by rayp on 2007-08-17
> **aquavitae said:**
> It could be a problem with a new kernel.  If you've had it for a year chances are its done a few kernel upgrades.  In grub, do you have anumber of ubuntu kernel options, e.g. 2.6.16, 2.6.17, 2.6.18?  If you do, try an older one and see if it gets anywhere.  Can you boot into recovery mode?
I assume you mean you've checked the file names against whats in menu.lst?

Yes I have tried all the options in the GRUB menu and none of them will boot.

Yes the file names stack up.  I did notice that menu.lst was showing them on hdb1 instead of hda1 which is what the drive appears to be now.  Changed menu.lst and re-installed grub.  now get...

Error 17: Cannot mount selected partition.

Ray

---

### Post by rayp on 2007-08-17
> **ramjet_1953 said:**
> Super GRUB disk is good for any sort of GRUB issue.

It is an iso that you burn to a CD.

You just boot from the CD and you can recover your GRUB install

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Regards,
Roger 8)

Thanks, I will try that ASAP.

Ray

---

### Post by aquavitae on 2007-08-17
When grub starts, go to the command line (I think you press 'c' - it tells you on the screen below the boot menu) and try ```
find /boot/grub/stage1
```It should tell you where grub is installed, in your case it should show```
(hd0,0)
```Btw, /dev/hda1 is (hd0,0) not (hd0,1).

---

### Post by rayp on 2007-08-18
> **aquavitae said:**
> When grub starts, go to the command line (I think you press 'c' - it tells you on the screen below the boot menu) and try ```
find /boot/grub/stage1
```It should tell you where grub is installed, in your case it should show```
(hd0,0)
```Btw, /dev/hda1 is (hd0,0) not (hd0,1).

Ahhh, yes you are right.  Don't know why I put (hd0,1).  I've changed menu.lst again and it boots okay now.

I am still stumped as to why this happened.  Could aptitude have updated something that reverted menu.lst back to it's original contents as before I installed the extra drives?

Anyway, many thanks for the help, I'm back up and running now.

Ray

---

### Post by medley on 2007-08-18
> **rayp said:**
> Hi,

I have had a Ubuntu 6.06 server installed and running for about a year and suddenly it will not boot up.  Grub returns an 'Error 15: File not found' when trying to load the kernel.

I have used aptitude regularly to update the system and ran an update yesterday.  Today I cannot boot.

I am quite new to Ubuntu and I don't really know what to do next.  I haven't moved the kernel files.

Can anyone give me a pointer, even if it is that I have posted this in the wrong forum :-)

Thanks,

Ray

For what it's worth, I don't do updates. Once I have a system working the way I like it, I leave it. Experience has taught me to be prepared for problems if I do an update. That's not to say that many people don't do many updates without problems, but I've spent enough time fixing things broken by an update that my current mantra is, 'if I don't need the update for a specific reason, don't touch it unless I have some time to spare to fix things." Not the message the community wants out there, I'm sure, but the practical truth.

---

### Post by Gremlinzzz on 2007-08-18
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15)

---

