---
title: "Windows drive died; need GRUB to boot from Linux drive"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Books on 2007-06-09
[SIZE="3"]My Windows drive (hda) just failed and I've disconnected it, but GRUB can't find Linux on my second drive (hdb), which I guess it thinks is hda.

My drives were configured as:
hda -- Windows
hdb -- Linux | FAT-32 partition

I've been booting GRUB from a floppy, and I'm accessing this site from a Kubuntu Feisty CD. How do I restore GRUB to boot the Kubuntu Edgy install on my working drive?

Also, how can I access the Kubuntu/FAT32 drive from the Feisty CD... is there a 'mount' command I need to give? Konqueror isn't recognizing the drive -- sudo fdisk -l  shows  "Unable to read /dev/sda"

Thank you!!!

Books[/SIZE]

---

### Post by confused57 on 2007-06-09
> **Books said:**
> [SIZE="3"]My Windows drive (hda) just failed and I've disconnected it, but GRUB can't find Linux on my second drive (hdb), which I guess it thinks is hda.

My drives were configured as:
hda -- Windows
hdb -- Linux | FAT-32 partition

I've been booting GRUB from a floppy, and I'm accessing this site from a Kubuntu Feisty CD. How do I restore GRUB to boot the Kubuntu Edgy install on my working drive?

Also... I don't know that much about Linux internals, so could you let me know step-by-step? :D

Thank you!!!

Books[/SIZE]
You can install grub to the hdb mbr, using the Kubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
following the tutorial, it would be something like this:
root (hdx,y)
setup (hdx)

of course, the x,y represent the hard drive & partition #'s

Then boot to your Ubuntu drive, if you get a grub menu, highlight your Ubuntu entry, press "e" change root from (hdx,y) to (hd0,y), then press "b" to boot...this temporary, if it works, but it can be made permanent.

You could probably do the "e" method with your grub floppy?

---

### Post by Books on 2007-06-09
> **confused57 said:**
> You can install grub to the hdb mbr, using the Kubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
following the tutorial, it would be something like this:
root (hdx,y)
setup (hdx)

of course, the x,y represent the hard drive & partition #'s

Then boot to your Ubuntu drive, if you get a grub menu, highlight your Ubuntu entry, press "e" change root from (hdx,y) to (hd0,y), then press "b" to boot...this temporary, if it works, but it can be made permanent.

You could probably do the "e" method with your grub floppy?

Hmmm... I entered GRUB and typed in 'find /boot/grub/stage1' like the directions say. It returns "Error 15: File not found" :(

---

### Post by confused57 on 2007-06-09
Have you tried "e" &  changing the root from (hd1,x) to (hd0,x), using your grub boot floppy?

If it doesn't work, you could mount your Ubuntu root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

I don't know if mounting your root partition & editing your root in your menu.lst would correct the error 15 when attempting to install grub to the mbr.

If you removed the hda drive when it failed, even though it doesn't work...it might work to reinstall the drive temporarily & try reinstalling grub to your hdb mbr.

---

### Post by Books on 2007-06-09
> **confused57 said:**
> Have you tried "e" &  changing the root from (hd1,x) to (hd0,x), using your grub boot floppy?

The "e" method? I looked at that thread and I can't find it... maybe it's been a long day ;)

---

### Post by Books on 2007-06-09
> **confused57 said:**
> Have you tried "e" &  changing the root from (hd1,x) to (hd0,x), using your grub boot floppy?

Oh, wait a minute... I haven't been able to mount my floppy. That may be the reason it can't find GRUB. What command do I use?

---

### Post by Books on 2007-06-09
**cat /etc/fstab ** shows this:

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0
```

**fdisk -l**  shows this:

```
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10337    78147688+   c  W95 FAT32 (LBA)
```

How can that be? The /etc/fstab for the Feisty floppy is /dev/sda6 but the fdisk is reporting /dev/sdb... there's only one drive connected. The other drive kept going thunk-thunk-thunk.

Is the reason it's not finding GRUB is that the floppy isn't mounted?

---

### Post by louieb on 2007-06-09
Is the fdisk -l in post #7 all of it? Was it run from the live CD?
Don't see a Linux install on it. 
Are you sure Linux wasn't on the drive that died?
How can the other drive go thunk, thunk if you unplugged it? Are you sure its unplugged?
As you noted your /etc/fstab does not match you fdisk output. 
What your saying and what I'm seeing don't match up. 
Before the hard drive  died:
What exactly did you do to boot windows?
What exactly did you do to boot Ubuntu?

The drive in fdisk shows a single fat partition. Is it data or could it be a win98 or a winXP install?

---

### Post by cantormath on 2007-06-09
The super Grub disk may make fixing this problem much easier.  its designed for this kind of problem.  It will scan for partitions and rewrite your MBR while keeping your installation intact.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by alienexplorers on 2007-06-09
Your /sdb1 drive is totally formatted in FAT.  Where is your linux ext2/ext3 partition.  Without one you are not going to be booting Linux.

---

### Post by Books on 2007-06-09
> **alienexplorers said:**
> Your /sdb1 drive is totally formatted in FAT.  Where is your linux ext2/ext3 partition.  Without one you are not going to be booting Linux.

Ah, it was picking up my external USB drive. ;)

Now the problem is why is it not detecting my good hard drive? I made sure it the drive is connected and the BIOS is recognizing it. I turned off the USB drive and now 'fdisk -l' returns nothing.

It's not finding the floppy, either.

---

### Post by louieb on 2007-06-09
Sometime it doesn't make a difference. but now you have one drive left. Is the jumper on the back set to cable select **CS** or master **MA**  it should be one or the other I would probably jumper the master pins. and is it pugged in to end of the flat ribbon cable with the red strip on the side closest to the power plug.

---

### Post by Books on 2007-06-09
> **louieb said:**
> Sometime it doesn't make a difference. but now you have one drive left. Is the jumper on the back set to cable select **CS** or master **MA**  it should be one or the other I would probably jumper the master pins. and is it pugged in to end of the flat ribbon cable with the red strip on the side closest to the power plug.

I followed your instructions and both aligned the pins and made sure the right cable was in, and 'fdisk -l' is still showing nothing. I rechecked the BIOS and it's identifying the drive correctly.

---

### Post by Books on 2007-06-09
> **Books said:**
> I followed your instructions and both aligned the pins and made sure the right cable was in, and 'fdisk -l' is still showing nothing. I rechecked the BIOS and it's identifying the drive correctly.

Wait, we're making progress...

I just followed the directions on [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351") and tried 'sudo grub' and it apparently put GRUB on the drive.

I rebooted and it showed the familiar GRUB screen I'm used to.

It's now showing "Error 21: Selected disk does not exist"

Wait... those directions were for restoring GRUB when the hard drive hadn't changed. How do you tell GRUB to switch drives?

---

### Post by confused57 on 2007-06-09
> **Books said:**
> Wait, we're making progress...

I just followed the directions on [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351") and tried 'sudo grub' and it apparently put GRUB on the drive.

I rebooted and it showed the familiar GRUB screen I'm used to.

It's now showing "Error 21: Selected disk does not exist"

Wait... those directions were for restoring GRUB when the hard drive hadn't changed. How do you tell GRUB to switch drives?
Are you getting the grub menu with the option to select Ubuntu...if you are, highlight your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), then press "b" to boot...

If you're not getting a grub boot menu...did you leave the hard drive connected to the slave position or did you reconnect it as master?

---

### Post by Books on 2007-06-09
> **confused57 said:**
> Are you getting the grub menu with the option to select Ubuntu...if you are, highlight your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), then press "b" to boot...

If you're not getting a grub boot menu...did you leave the hard drive connected to the slave position or did you reconnect it as master?

I'll try it.

Here is the output of the GRUB instructions I followed:

```
grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

Does this change any of what you suggested? Thank you!

---

### Post by confused57 on 2007-06-09
Yes it does, your hard drive is already recognized as (hd0)...it still might be a bios issue, you might need to turn the other IDE controller to "off" & the IDE controller to which you have your Ubuntu drive connected to "auto", possibly "enabled" or "on".

There are some other possible solutions in this link:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

Added: By other IDE controller, I didn't mean your IDE2 controller, but the IDE1 hd controller that doesn't have a hard drive attached...just wanted to clarify this.

---

### Post by louieb on 2007-06-10
One other thing to check for: Where  the flat ribbon cable plug into the mother board.  There could be two IDE connectors (most common)  they should be labeled ide0 and ide1 make sure the the flat cable is plugged into the connector labeled ide0.   
I just find it strange that GRUB can setup the hard drive but won't boot to the menu.:confused: oh well go figure. confused57 suggestions about checking the BIOS setup will probably get you to the grub menu.

---

### Post by Books on 2007-06-11
> **louieb said:**
> I just find it strange that GRUB can setup the hard drive but won't boot to the menu.:confused: oh well go figure. confused57 suggestions about checking the BIOS setup will probably get you to the grub menu.

Ok, we're getting closer. GRUB is now being recognized and it tries to boot, and the Kubuntu logo comes on the screen. But then it freezes. I'm wondering if it's the /etc/fstab or some other file.

I followed some of the directions here - [http://ubuntuforums.org/showthread.php?t=436541](http://ubuntuforums.org/showthread.php?t=436541) - and mounted the root partition.
```
sudo mkdir /media/kubuntu
sudo mount -t ext3 /dev/sda1 /media/kubuntu    
```

Then I tried...
```
kdesu /media/kubuntu/boot/grub/menu.lst
```
And it says '/media/kubuntu/boot/grub/menu.lst: Permission denied'

What files are making Kubuntu not finish booting, and how do I get to them? I'm working off the Kubuntu-Feisty CD which doesn't have a SUDO password (that I know of).

Thank you!

---

### Post by louieb on 2007-06-11
i think your right and the  /etc/fstab needs fixing. 
it uses uuid to find the uuid of your partitions ```
ls -l /dev/disk/by-uuid/
```And your right The Dapper live CD sudo does not have a password i guess its the same for Edgy and Feisty.  Now you just have to  figure out how to edit it.

---

### Post by Books on 2007-06-11
> **louieb said:**
> i think your right and the  /etc/fstab needs fixing. 
it uses uuid to find the uuid of your partitions... And your right The Dapper live CD sudo does not have a password i guess its the same for Edgy and Feisty.  Now you just have to  figure out how to edit it.

Ok, I found out how to access /etc/fstab by following the directions here [http://ubuntuforums.org/showthread.php?p=2826975](http://ubuntuforums.org/showthread.php?p=2826975) in post #21...

```
sudo mkdir /media/kubuntu
sudo mount -t ext3 /dev/hda1 /media/kubuntu
gedit /media/kubuntu/etc/fstab
cd /media/kubuntu/etc
sudo cp fstab fstab_backup
gksudo gedit /media/kubuntu/etc/fstab
```


Here's the original **/etc/fstab** with the "UUID"s replaced since I'm not sure if it's some kind of password...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=*{bunch of garbage code}* /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb6
UUID=*{bunch of garbage code}* none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hda1       /media/windows ntfs  nls=utf8,umask=0222 0    0
# /dev/hda5       /media/g_part  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb5       /media/f_part  vfat    iocharset=utf8,umask=000   0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
```

**sudo fdisk -l** shows...

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4444    35696398+  83  Linux
/dev/sda4            4445        9732    42475860    f  W95 Ext'd (LBA)
/dev/sda5            4633        9732    40960048+   b  W95 FAT32
/dev/sda6            4445        4632     1510047   82  Linux swap / Solaris

```

I don't know why it's showing /dev/sda... they are IDE drives, but if I remember right it had something to do with the kernel at the time of the Feisty release.

Anyway, I know to change '/media/f_part' from '/dev/hdb5' to '/dev/sda5'. But what about all that UUID garbage... the '# /dev/hdb1' and '# /dev/hdb6' is all commented out. How can I update it to not point at a non-existent drive?

Thank you!!!

---

### Post by louieb on 2007-06-12
You have some stuff you called bunch of garbage code.   

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID={bunch of garbage code} [COLOR="Red"]/ [/COLOR]              ext3    defaults,errors=remount-ro 0       1
# /dev/hdb6
UUID={bunch of garbage code} none            [COLOR="Red"]swap[/COLOR]    sw              0       0

```
you need to replace the garbage code. use the ls -l... command I mentioned earlier
for your [COLOR="Red"]/ [/COLOR]partition use the uuid for .dev/sda1
and for your [COLOR="Red"]swap[/COLOR] use the uuid of /dev/sda6

for now that should be all you need you can comment out anything else. Try that and see if that gets it going.

---

### Post by Books on 2007-06-13
> **louieb said:**
> You have some stuff you called bunch of garbage code.

you need to replace the garbage code. use the ls -l... command I mentioned earlier
for your [COLOR="Red"]/ [/COLOR]partition use the uuid for .dev/sda1
and for your [COLOR="Red"]swap[/COLOR] use the uuid of /dev/sda6

for now that should be all you need you can comment out anything else. Try that and see if that gets it going.

Oh, the "garbage code" was the UUID. I checked the codes and they are correct, the same as the ls -l... command you suggested.

When I turn on the system GRUB comes up, and pressing "e" it incorrectly shows hd(1,0) when it should be hd(0,0)... I think, and the drive as hdb1 when it should be sda1. I correct them and press "b" to boot, and it goes to the Kubuntu splash screen and freezes there.

---

### Post by louieb on 2007-06-13
ok two last thing to try and I'm out of ideas
Your right about needing to change the root to (hd0,0) and while your in GRUB edit also edit the kernel line and remove the **quiet splash** 
This will let a bunch of messages print.  may be you can get an idea of where and why it stops booting..

The 2nd thing to try is in /etc/fstab comment out everything **but the / and swap** lines and see if its hanging trying to process one of them.

---

### Post by Books on 2007-06-18
> **louieb said:**
> ok two last thing to try and I'm out of ideas
Your right about needing to change the root to (hd0,0) and while your in GRUB edit also edit the kernel line and remove the **quiet splash** 
This will let a bunch of messages print.  may be you can get an idea of where and why it stops booting..

The 2nd thing to try is in /etc/fstab comment out everything **but the / and swap** lines and see if its hanging trying to process one of them.

I deleted the "quiet" in GRUB and it gave a clue to where it was hanging. It wasn't finding the root partition. So on a whim I changed "sda1" in the grub boot option to "hda1" and it booted and appears to be working. :popcorn:

Last question: How do I edit GRUB permanently so I don't have to edit it every time I boot?

Thank you to everyone who helped... you really came through for me!

---

### Post by confused57 on 2007-06-18
Good catch, glad you got it working...yes, the kernel root has to be pointing to the correct device, also.

Open a terminal(Applications---Accessories---Terminal):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
make your changes, then quit & save

Also make sure to change your groot & kopt options:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
see the pertinent sections in this link

---

### Post by Books on 2007-06-18
> **confused57 said:**
> Good catch, glad you got it working...yes, the kernel root has to be pointing to the correct device, also.

Open a terminal(Applications---Accessories---Terminal):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
make your changes, then quit & save

Uh, oh. The /boot/grub/menu.1st is an empty file. Before the crash of the windows hard drive I was booting from GRUB on a floppy. I looked at the original boot floppy in Konqueror and nothing is showing up (with hidden files showing)... is a menu.1st file on the floppy?

---

### Post by confused57 on 2007-06-18
> **Books said:**
> Uh, oh. The /boot/grub/menu.1st is an empty file. Before the crash of the windows hard drive I was booting from GRUB on a floppy. I looked at the original boot floppy in Konqueror and nothing is showing up (with hidden files showing)... is a menu.1st file on the floppy?
Not to worry, menu.lst is short for menu.list, not menu.first...if you typed menu.first, a blank file would open.  The grub floppy probably just contains the grub IPL:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

