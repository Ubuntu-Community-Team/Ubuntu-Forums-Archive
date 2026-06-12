---
title: "installation: OS X + multi-linux"
date: 2009-06-12
forum: Apple Hardware Users
---

### Post by v41 on 2009-06-12
How difficult is it to install OSX + multiple flavors of Ubuntu on a single hard-drive?  If it's fairly easy, then could you provide a link to some instructions?  At present I have a standard setup with 4 partitions; EFI, OSX, Intrepid and Swap.    Could this be reconfigured as 3 partitions -- EFI, OSX and Extended --  with Extended being subdivided into Logical Partitions containing several flavors of Ubuntu + Swap?

---

### Post by majamba on 2009-06-12
well it is prety easy as long you don't bother putting up windows on one of partitons

refit tends to work pretty well

---

### Post by v41 on 2009-06-12
> **majamba said:**
> well it is prety easy as long you don't bother putting up windows on one of partitons.  Refit tends to work pretty well

Sounds promising!  I was hoping that it would be straightforward, but a google search didn't turn up any instructions so I became suspicious that there might be a problem.

(I do have Refit and Grub installed, and don't plan on installing Windoze.)

---

### Post by cyberdork33 on 2009-06-12
You cannot create extended or logical partitions on a GPT disk. 

OSX and your additional Linux partitions other than the "bootable" one can be on a partition greater than #4 no problem.

I think the work around for this that most people use is to create a single /boot partition for all your distros.

---

### Post by v41 on 2009-06-16
Cyberdork33, thanks for clearing up my confusion about partitions!

Unfortunately  I don't yet comprehend your comment that > I think the work around for this that most people use is to create a single /boot partition for all your distros.

At present OS X and Intrepid are installed, and  I'd like to install Jaunty.  Could this be done by first shrinking the Mac and Intrepid partitions using GParted, and then installing Jaunty from a CD to the largest area of free space on the disk?   Could Intrepid and Jaunty use the same swap partition?  Would there be a problem with having one copy of Grub on the Intrepid partition, and a second copy on the Jaunty Partition?

---

### Post by cyberdork33 on 2009-06-16
> **v41 said:**
> Unfortunately  I don't yet comprehend your comment
You can create a single /boot partition for all your linux installations. You would have grub and the kernels for your distros there and you would use grub to choose to boot into either Ubuntu or whatever other distro.

> **v41 said:**
> At present OS X and Intrepid are installed, and  I'd like to install Jaunty.  Could this be done by first shrinking the Mac and Intrepid partitions using GParted, and then installing Jaunty from a CD to the largest area of free space on the disk?
Yes... though I would not choose the "install to the largest free space" option for this. I would use the manual partitioner to create a new root partition for jaunty (making sure it was one of the first 4!) and installing as normal with grub on the new partition. There will not be any obvious way to discern between the two installs of grub in rEFIt other than looking at the partition number you are booting from.

> **v41 said:**
> Could Intrepid and Jaunty use the same swap partition?
Certainly. In fact, I would recommend you do that. The only time this is an issue is if you use the hibernate function (suspend to disk) in one distro, then boot with the other when you turn your computer on. Not sure what the outcome would be, but you would lose whatever was on the swap partition I am sure. If you don't use hibernate (most don't) then this is not a problem.

> **v41 said:**
> Would there be a problem with having one copy of Grub on the Intrepid partition, and a second copy on the Jaunty Partition?Nope other than what I mentioned above about rEFIt.

**[COLOR=Red]NOTE: Please make sure to BACKUP everything before adjusting your partitions. Even on a good day this can lead to data loss.[/COLOR]**

---

### Post by v41 on 2009-06-16
Thanks Cyberdork33!  I'll give it a try.

> I would use the manual partitioner to create a new root partition for jaunty (**making sure it was one of the first 4!**) and installing as normal with grub on the new partition.

Hmmm... I'm confused as to why the first four partitions are special on a GPT disk?

---

### Post by cyberdork33 on 2009-06-16
> **v41 said:**
> Hmmm... I'm confused as to why the first four partitions are special on a GPT disk?
The first 4 partitions are the partition listed in the emulated MBR partition table. Unfortunately, this is the table that grub currently uses to boot Ubuntu, so if it is not listed there, you cannot boot it!

---

### Post by v41 on 2009-06-16
> The first 4 partitions are the partition listed in the emulated MBR partition table. Unfortunately, this is the table that grub currently uses to boot Ubuntu, so if it is not listed there, you cannot boot it!.

Aha!  I think this is what I half-remembered when posting the original question at the top of the thread.  Now I understand why people want to find an alternative to grub.  Speaking of which, I read that Karmic will use grub2, though I don't know whether it also uses the MBR partition  table.

---

### Post by cyberdork33 on 2009-06-16
> **v41 said:**
> .

Aha!  I think this is what I half-remembered when posting the original question at the top of the thread.  Now I understand why people want to find an alternative to grub.  Speaking of which, I read that Karmic will use grub2, though I don't know whether it also uses the MBR partition  table.
grub-efi boots using the native EFI process... i.e. more like OS X. However, there are some bugs to work out when booting that way. I am unsure if the normal version of GRUB2 reads the GPT or not.

---

### Post by pxwpxw on 2009-06-17
Grub2-pc can even load linux kernels from hfsplus i.e. the Mac OSX partition, and speaks GPT but has bootcode still on the MBR,.
The karmic grub2 packages <1.96+20090523-1ubuntu1_amd64.deb> are up to svn rev 2233 and look good. IDK which is the default install for karmic, just about to find out.
EDIT:
The alternate install amd64 installs grub-legacy, but the grub2 grub-pc package is easy to install and setup (it removes grub1). And it works (installed from sda8 to MBR and booting sda4...sda10).

---

### Post by cyberdork33 on 2009-06-17
> **pxwpxw said:**
> Grub2-pc can even load linux kernels from hfsplus i.e. the Mac OSX partition, and speaks GPT but has bootcode still on the MBR,.
Does this mean we are still limited to the first four partitions when booting legacy mode?

> **pxwpxw said:**
> The karmic grub2 packages <1.96+20090523-1ubuntu1_amd64.deb> are up to svn rev 2233 and look good. IDK which is the default install for karmic, just about to find out.
I believe the plan is to make grub2 default in the final release.

The fact that it replaces Grub1 is interesting too. It used to install along side grub1 in previous editions, and it would leave a menu option to boot grub1.

---

### Post by pxwpxw on 2009-06-17
> **cyberdork33 said:**
> Does this mean we are still limited to the first four partitions when booting legacy mode?
No, both grub1 and grub2 can boot linux kernel from any partition, but have the grub stage1 or grub2 boot.img on the MBR. 

> 
The fact that it replaces Grub1 is interesting too. It used to install along side grub1 in previous editions, and it would leave a menu option to boot grub1.
It still does offer to leave grub1 for transition, I chose not to do that since I had no working grub1 at that stage.

---

### Post by cyberdork33 on 2009-06-17
> **pxwpxw said:**
> No, both grub1 and grub2 can boot linux kernel from any partition, but have the grub stage1 or grub2 boot.img on the MBR. 
Hmm interesting. I didn't know it was that specific. So you can theoretically put the stage files on the EFI partition and you can install Linux anywhere...?

> **pxwpxw said:**
> It still does offer to leave grub1 for transition, I chose not to do that since I had no working grub1 at that stage.
OK, interesting

---

### Post by pxwpxw on 2009-06-17
I have not tried it yet but there is some explanation about grub2 second stage = core.img,  and possible locations in this interesting page in the grub wiki -

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

---

### Post by v41 on 2009-06-18
Thanks to CyberDork33, OS X + Intrepid + Jaunty is triple-booting bootylishiously with Refit  & Grub:p

It sounds as though Grub (grub1) will soon be obsolete, but I'll nevertheless post a summary in case it is helpful.  I began with a dual-boot OS X + Intrepid setup, and wanted to change it to triple-boot OS X + Intrepid + Jaunty.

(i) Setup the following partitions using GParted: (1) EFI/MBR (2) OS X (3) Intrepid (4) Jaunty (5) Swap

(ii) Update /etc/fstab on Intrepid to incorporate the new partitioning scheme.  It makes use of UUID's which can be found by running,

 sudo blkid

(iii) Install Jaunty.

(iv) To find where Grub is installed on the system, download and run the boot information script,

 [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

We want one copy of Grub on the Intrepid partition, another copy on the Jaunty partition,
and we do NOT want a copy on the EFI/MBR partition. 

If Grub is not installed on Intrepid, then install it as shown here:

 [http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

 [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Ditto for Jaunty.

If Grub is installed on the EFI/MBR partition, then delete it as shown here:

  [http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

(v) Upon rebooting and entering the REFIT menu, select the "sync the partition table" option.


Many thanks to CyberDork33 who wrote several of the above guides.

---

