---
title: "VirtualBox and &quot;Fatal. Could not read from the boot medium&quot; message"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Proshka on 2007-12-21
The message below was posted 5 days ago in the Virtualization forum, the obvious location for a problem of this kind. Since nobody read it until today, I hope to be luckier on this forum.

I want to use an original Win98 CD under VirtualBox to make my scanner work (a Lexmark). I managed to install VB without any trouble, gave 128 Mb RAM and 2 Gb disk space to the virtual disk, started, pressed F12, selected the CD-ROM option from the VirtualBox temporary boot menu and ended having this message: "Fatal. Could not read from the boot medium. System halted." I have also tried Qemu and VMWare (same results) and even burned another ISO, to no avail.

I am running Gutsy on a Toshiba Satellite A75-S226 (3.06 MHz processor,  512 Mb RAM, 1Gb swap).

---

### Post by puccaso on 2007-12-21
well im assuming when u ran with qemu you ran with

-cdrom /dev/cdrom (or whatever ur cdrom is) -boot d to boot from cdrom..

or in vbox, u selected the cdrom to boot.

now if u've done all this - and ur system still doesnt boot from the cd.. then i fear
ur cd may not be bootable.

are you able to boot your installation cd natively?

---

### Post by Proshka on 2007-12-21
Thanks for your quick response. Yes, the cd boots fine natively.

---

### Post by puccaso on 2007-12-21
ok. the cd boots fine natively.

have you tried ripping an iso from the cd and using that?

try this

sudo -s
cd /tmp
dd if=/dev/cdrom of=/tmp/xp.iso

it will rip an iso of ur cdrom

now try using that to install from.

---

### Post by anewguy on 2007-12-21
Be double sure you can really boot your PC with the Windows 98 CD (try it - you can just power off or ctrl/alt/del before it will ever do anything to your disk), because it sounds like VirtualBox is just telling you there is nothing there to use as boot information.

I say this from experience - my Windows 98 CD requires a diskette to boot, then LOADS Windows 98 from the CD.  You can install from the CD as long as you have booted the PC first.  I know that apparently some Windows 98 CDs were bootable, but I never ran into one. You can download an image of the boot floppy from many places on the internet, then instead of writing it to a floppy just point VirtualBox to use the image as the boot device (at least you can do that it VMWare anyway).

I also used the diskette image and the Windows 98 CD and built a bootable Windows 98 installation CD.

---

### Post by puccaso on 2007-12-21
he has a point actually
but the win98se never had that problem.
and seeing as his sytem books natively, then it shouldnt have that problem.

---

### Post by Proshka on 2007-12-21
Pucasso, I followed your instructions and the results are the same.
Anewguy, the cd boots normally without any diskette.

---

### Post by Proshka on 2007-12-23
Same problem trying to boot XP from a cd.

---

### Post by The Cog on 2007-12-23
You usually have to tell VirtualBox to connect to the CD-ROM drive. It's under the Device menu I think. Do this after the CD has been inserted in the drive, then use the manu to reset the VM.

---

### Post by Proshka on 2007-12-23
No matter how I tell VM to read from the cd, it fails. The thumbnails show the situation before, while and after trying to boot from the cd.

---

### Post by The Cog on 2007-12-23
I see. This may sound odd, but try configuring the virtual machine not to mount the cd-rom. Then once the VM is running, insert the CD, wait for the nautilus window to appear, and then select Devices->Mount CD/DVD-ROM->Host drive /dev/cdrom. That's the way I use VB, and it works fine for me that way.

---

### Post by Proshka on 2007-12-23
Hi Cog, 
Thanks for your help. I followed your instructions but unfortunately the problem is still there.

---

### Post by puccaso on 2007-12-23
ok
can you download some other bootable iso

like the ubuntu jeos image
its about 100 meg, or something like dsl 

just to see if it can boot from those images.

we have to diagnose where the problem is, hardware  - ur system or the cd - or the software itself..

---

### Post by shareMenaPeace on 2007-12-23
this fixed it to for me - other iso file ....

---

### Post by Proshka on 2007-12-23
Well, things are improving; I could boot the ISO (and even run a memory test from it).

---

### Post by Proshka on 2007-12-24
I got another ISO for Win98 and then booted the image from the hard disk. The installation begun normally but I got a message saying I do not have enough RAM. According to other postings, 128 Mb should be enough to run Win98 under Ubuntu with 512 Mb. I wonder why it still does not work for me.

---

### Post by destructaball on 2008-05-15
if im right ur gonna really kick ureself for going ot all this trouble, i had exactly the same problem and im sorta noobish, it took me a while to work out that you have to go to devices, mount cd/dvd rom then click host drive...... then try and mount the disk, it works, tho that does seem overly simple and i may have had a different problem

---

### Post by JFQueralt on 2008-06-16
In my case I realized my Dell server had a virtual drive and thus was mounting that one instead of the physical one.
Swapped and everything was good.

Maybe it helps somebody.

Jean.

---

