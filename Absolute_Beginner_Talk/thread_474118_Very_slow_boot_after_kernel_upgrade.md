---
title: "Very slow boot after kernel upgrade?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by words1 on 2007-06-14
Since the last kernel update, my computer takes forever to boot.  Any ideas?  Open Office also takes much longer to load.

Dell 4700 running 7.04, P4 3gHz, 2 gigs of ram.  Two sata drives.

---

### Post by FleetAdmiral74 on 2007-06-14
Does it still boot slow when you boot the old kernel?

---

### Post by words1 on 2007-06-14
yes.  we're talking ~3-4 minutes versus ~45-60 seconds before.  The orange bar hangs right at the start, sits there for a long time, but when it starts to move, boot is almost normally fast.

---

### Post by Rocket2DMn on 2007-06-14
There is a way to show the services that are loading rather than Ubuntu's splash screen when the computer is booting.  If you can get this, you can see what is taking so long and troubleshoot from there.
A common villain is the network trying to connect.

---

### Post by Austin_KW on 2007-06-14
Install bootchart

sudo apt-get install bootchart

then reboot, and look in /var/log for the graphical display of the boot process, you will probably see somewhere without cpu or disk activitity, scroll down and look for the process starting at this idle time

Edit; You can also boot the old kernel and compare the charts, The timing difference should be obvious

---

### Post by words1 on 2007-06-15
OK, I posted the chart to [www.evanmorris.com/feisty-boot.png]("http://www.evanmorris.com/feisty-boot.png").

It hangs for just about two minutes with scsi_eh_0 and modprobe in pink.

When I tried to boot in the old kernel this morning, it dumped me into intrafms or something and I had to reboot.  It was the same message I got when I originally tried to install 7.04 on this machine, which may be a clue.  7.04 wouldn't install, the live disk wouldn't even run.  I had been using 6.06, so I installed 6.10 and upgraded to 7.04 from there.  It worked fine until now.

Thanks for any help you can give!

---

### Post by Rocket2DMn on 2007-06-15
Sounds like it may be looking for SCSI hard drives that you don't have.  There is probably a way to disable this check (or at least tweak it correctly) so that it doesn't waste all that time searching for something that isn't there.  Perhaps somebody else here knows how.  
This is why networking is also a common problem on bootup for some people.

---

### Post by drs305 on 2007-06-15
When I installed the latest kernel it changed a few of my data drives/partitions in fstab from sda's to hda's. I had to go into fstab to correct things. Are all yours still labled correctly and still working?

---

### Post by words1 on 2007-06-15
Hard to say.  Here it is.  I also just noticed that my DVD drive isn't working.

sda1 is the second hard drive, mounted at /sda



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=4906feaa-861a-44b0-b6c7-68ed24ce73d9 /               ext3    defaults,errors=remount-ro 0       0
# /dev/sdb5
UUID=9c04091c-a648-49cf-afd8-e3a529ad78fd none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda1    /sda   ext3    defaults     0        2

---

### Post by Rocket2DMn on 2007-06-15
My drives changed after some random updates a few days back (kernel may have been included - i DID have to restart).  The drives went from hda to sda (which is wrong).  I'm hoping they put a fix out for it, but at least it still works.  However, I don't experience a slow bootup.

---

### Post by Austin_KW on 2007-06-15
> **words1 said:**
> OK, I posted the chart to [www.evanmorris.com/feisty-boot.png]("http://www.evanmorris.com/feisty-boot.png").

It hangs for just about two minutes with scsi_eh_0 and modprobe in pink.

When I tried to boot in the old kernel this morning, it dumped me into intrafms or something and I had to reboot.  It was the same message I got when I originally tried to install 7.04 on this machine, which may be a clue.  7.04 wouldn't install, the live disk wouldn't even run.  I had been using 6.06, so I installed 6.10 and upgraded to 7.04 from there.  It worked fine until now.

Thanks for any help you can give!

Oh that looks nasty, Anything from dmesg (a few seconds in)

What about temporarily disconnecting the second drive and the cdrom?

---

### Post by words1 on 2007-06-16
I disconnected the cd-rom drive and it booted properly.  See [http://www.evanmorris.com/feisty-boot2.png]("http://www.evanmorris.com/feisty-boot2.png")

Much better. Thanks to all!  

Then I did a fresh install of 7.04, which worked!

---

### Post by Austin_KW on 2007-06-16
Can you reattach the cd-rom drive after the fresh install?

I noticed an unconfirmed bug for an older cd drive, you may want to add your comments  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115915](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115915)

---

