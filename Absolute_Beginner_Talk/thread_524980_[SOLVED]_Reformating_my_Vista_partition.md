---
title: "[SOLVED] Reformating my Vista partition"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by amazingtaters on 2007-08-13
Hokay, so I want to reformat my ntfs vista partition, but I've got a question that I want answered before I delve into this. This is what GParted shows, and I want to know if it will be okay to repartition the ntfs drive sda2, since it is flagged as the boot partition. Here's an ss to show you what I mean. Ploz help.

[IMG]http://i13.photobucket.com/albums/a287/BFEtatersalad/Screenshot.png[/IMG]

---

### Post by amazingtaters on 2007-08-13
bumping, HALP PLOZ

---

### Post by Arthur Archnix on 2007-08-13
Bumping after 20 minutes? Perhaps the IRC channels would be a better forum to ask your question in , if you're looking for immediate response.

I'd read somewhere else that you should do as much as possible of the resizing from within vista. It takes it down by half, reboot, down by half, reboot, and so forth. Apparently MS puts some marker at the halfway point so that it can only go down by half safely. I'd at least try that before using gparted to resize. Certainly defrag your harddisk before and after each resize. 

But no, the fact that it is boot doesn't matter in terms of resizing it. It's all about how you resize it, using what program, and whether or not you've defragged.

---

### Post by omegamike3 on 2007-08-13
are you wanting to keep the partition but just reformat it to something other the NTFS? or do you want to get rid of the partition completely and just have one, single partition?

---

### Post by amazingtaters on 2007-08-13
I wanna completely reformat it, to an ext3, not just make it smaller. And I was on second page, which I've seen kill many an unreplied to thread. Basically I want to keep the partition, but have it formatted as and ext3

---

### Post by omegamike3 on 2007-08-13
> **amazingtaters said:**
> I wanna completely reformat it, to an ext3, not just make it smaller. And I was on second page, which I've seen kill many an unreplied to thread. Basically I want to keep the partition, but have it formatted as and ext3

Nice... then just tell gparted that you want everything currently ntfs to be ext3, raise your hands to the sky in a thunderous and biblical sort of way and it shall be done! or you know, click 'ok' :)

---

### Post by amazingtaters on 2007-08-13
I like the thunderous, bliblical thing. Hold on, lemme go get my smoke machine and thunder sound maker thing. And uh, do I hafta unmount it first? I've never partitioned with GParted, I've always used Paragon Pro

---

### Post by omegamike3 on 2007-08-13
technically, I don't believe you actually need to unmount the drive, but you could always just run gparted from the live cd and not worry about it ;)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
here's some fine documentation straight from the horse's mouth about resizing. it really is beautiful, just drag the arrow to make it bigger... brings a tear to my eye...8-[

---

### Post by amazingtaters on 2007-08-14
I did some more snooping around the intarwebs, and it appears that my boot loader, the grub we all know and love, is installed on that partition. So basically what that means for me is that unless I can move the boot loader to a different partition, say my ext3 partition that ubuntu is already using, I cannot wipe the partition and reformat it. So, any way to move grub?

---

### Post by amazingtaters on 2007-08-14
Ok, so my grub files are indeed on my linux filesystem under the boot folder. There are no grub files on my windows partiton. I'm thinking this means that I'll be okay if I delete the ntfs windows partition. Agree, disagree?

---

### Post by Arthur Archnix on 2007-08-14
Download a grub live cd before you do this. If something goes wrong and you can't reboot, the grub cd will reinstall the bootloader. Having it around has saved me once before.

---

### Post by meierfra on 2007-08-14
Grub is installed in two pieces:

1. In the MBR (Master Boot Record) This is the very first part of the hard drive, even before the first partition. 

2. inside /root  . In your case /root is part of your linux partition. ( But some people place /root on a separate partition)

So  reformating your NTFS partition will not destroy your boot loader.

---

### Post by amazingtaters on 2007-08-14
so then with the grub livecd I will be able to boot up ubuntu just like before and install grub to whichever partition I so desire?

---

### Post by amazingtaters on 2007-08-14
> **meierfra said:**
> Grub is installed in two pieces:

1. In the MBR (Master Boot Record) This is the very first part of the hard drive, even before the first partition. 

2. inside /root  . In your case /root is part of your linux partition. ( But some people place /root on a separate partition)

So  reformating your NTFS partition will not destroy your boot loader.

This is so even though the partition has a boot flag on it?

---

### Post by meierfra on 2007-08-14
> Download a grub live cd before you do this. 

Good recommendation.  You should not need it, but partitioning is always risky. You shouls also backup any valuable data on your linux partition.

---

### Post by meierfra on 2007-08-14
> this is so even though the partition has a boot flag on it?

Yes, the boot flag means that you can boot that partition. Also  it contains information  to boot the NFTS partition, but not for booting the linux partition.

(For some strange reason only NFTS partitions need a boot flag to be bootable, linux partition do not)

---

### Post by meierfra on 2007-08-14
> so then with the grub livecd I will be able to boot up ubuntu just like before and install grub to whichever partition I so desire?

yes,  but if everything goes well, ubuntu should boot up without the need of the Grub Live CD.
(but parts of grub will always go to the MBR)

---

### Post by amazingtaters on 2007-08-14
ok, well I am getting pretty tired. I've downloaded a .bz2 of the SuperGrubDisc iso and I'll burn it off tomorrow, then I'll try this format. Now, I've gotta get some sleep.

---

### Post by amazingtaters on 2007-08-14
New problems in the wirlde of reformatting. I booted via livecd and managed to reformat that pesky ntfs partition (/media/sda2) to an ext3 partition. However, when I now try and mount it, I get the error Unable to Mount Volume, with details reading mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /). 

So, what's the deal now guys?

---

### Post by Arthur Archnix on 2007-08-14
Truthfully, I've never done what you're trying to do. If you want to change the partition to ext3, why not just delete it, and then expand the linux partition? Unless you wanted it as a separate partition for a reason. 

Give this some time though. Deleting and resizing takes time, it's possible someone will have a quicker solution.

---

### Post by amazingtaters on 2007-08-14
Had a look at various posts and whatnotery pertaining to mounting hdds and I think I've got a guess as to why I cannot mount this drive. Basically, had a look at my fstab file, and under sda2, which is the drive I've reformatted, it lists the mount point as /media/sda2 but the type as ntfs-3g. Could this discrepancy, with the partition now being ext3 and fstab still treating it as an ntfs, be causing my woes?

---

### Post by meierfra on 2007-08-14
Are you  able to boot into ubuntu (without the live cd)?

If yes, do that and post the output of


```
 sudo fdisk -l
```

and 

```
cat /etc/fstab 
```

---

### Post by amazingtaters on 2007-08-14
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2            1020        7826    54677227+  83  Linux
/dev/sda3            7827       14513    53713327+  83  Linux
/dev/sda4           14514       14593      642600   82  Linux swap / Solaris

```

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=d2af7b5b-bef7-48bc-aab0-c5c1f197edc3 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=BEB8486716D9B5D2 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda2 :
UUID=A4E40FFDE40FD10A /media/sda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda4 :
UUID=d49535b1-9298-4c2f-aad8-15672fa09a29 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

```

---

### Post by Arthur Archnix on 2007-08-14
> **amazingtaters said:**
> Had a look at various posts and whatnotery pertaining to mounting hdds and I think I've got a guess as to why I cannot mount this drive. Basically, had a look at my fstab file, and under sda2, which is the drive I've reformatted, it lists the mount point as /media/sda2 but the type as ntfs-3g. Could this discrepancy, with the partition now being ext3 and fstab still treating it as an ntfs, be causing my woes?

Nice job taters. Me thinks you're on your way your way to helping others!

EDIT: Your post was too quick for me! 

Change sda2 to ext3

---

### Post by amazingtaters on 2007-08-14
> **Arthur Archnix said:**
> Nice job taters. Me thinks you're on your way your way to helping others!

I do try. It's always best to look around a bit, and then ask for help, then look some more. If I keep going in one direction I'll read myself to death and look at the wrong things, wasting tons of time. If I keep asking questions other people keep me focused on finding out the right way to do things. That's why I love these forums so darn much.

---

### Post by meierfra on 2007-08-14
> Basically, had a look at my fstab file, and under sda2, which is the drive I've reformatted, it lists the mount point as /media/sda2 but the type as ntfs-3g. Could this discrepancy, with the partition now being ext3 and fstab still treating it as an ntfs, be causing my woes?

yes.  But I don't have anymore  time right now to help you. Maybe somebody else with help you or you might just   find the solution yourself.

---

### Post by amazingtaters on 2007-08-14
so basically I think I need to edit the enty in fstab. But dang that's such an important file, I don't wanna really mess something up. I guess I'm off to do more research so that I don't do something stupid.

---

### Post by Arthur Archnix on 2007-08-14
Don't worry about it taters...

Editing sda2 will only make it unusable if you mess it up. It's already unusable!

Ok, here, do this.

Use the mount command to mount sda2. If it works, you can make the change I suggested above. 

type mount in the terminal and see if sda is mounted anywhere. if it is type
```
sudo umount /dev/sda2
```
Then, make a temporary tplace for it in mnt.
```
sudo mkdir /mnt/temp
```
now try mounting it.
```
sudo mount /dev/sda2 /mnt/temp
```
if no errors show up, and your able to cd to /mnt/temp then you know that changing sda2 to ext3 in your fstab will be ok!

I'm not sure, but your fstab may mess up the mount command. If so try:
```
sudo mount -t ext3 /dev/sda2 /mnt/temp
```
But from what I understand mount will automatically try to detect the FS type.

PS. Be sure to send meierfra a thank you. He helped you out a lot, and rightly or wrongly, appears  to feel like it was unappreciated. His fstab comment though just saved you at least two hours of following my deleting the partition and resizing advice! :)

---

### Post by amazingtaters on 2007-08-14
Did all of that, and the drive mounted to /mnt/temp. I cd'd to /mnt/temp with no errors. Only problem now is that I don't have permission to write to the drive.

---

### Post by Arthur Archnix on 2007-08-14
That's easy. Don't worry about it. Make the change to fstab, then search the forums for chown.

---

### Post by amazingtaters on 2007-08-14
> **Arthur Archnix said:**
> That's easy. Don't worry about it. Make the change to fstab, then search the forums for chown.

k. I hadn't had time to search the forums yet, but I'll look for chown.

---

### Post by amazingtaters on 2007-08-15
Ok, got my permissions sorted out. Thanks a lot to everyone who helped me through this. I mean, HUGE HUGE thanks. I'm trying to get ready to move to college this weekend and getting some last minute computer stuff done has been stressing me out. So once again, many thanks to all, and maybe some kookies later!

---

