---
title: "Cant access Windows after installing ubuntu"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by nayana on 2007-07-10
Hi,

Ive never installed a linux distribution before and was very excited when I installed Ubuntu today...but the excitement was short lived as I restarted my machine and realized that I dont have windows on GRUB. I followed the steps on the ubuntu site for dual boot and allowed the installer to resize my partitions. Any idea what happened? did the installer overwrite my MBR? when I do "df", or check fstab, i dont see any partitions other than /dev/sda1...have i lost all my data that was on my windows partition? is there anyway i can recover windows? I read in one thread about creating a rescue CD, is there anyway i can recover using the ubuntu installation CD?

Thanks!

---

### Post by alienexplorers on 2007-07-10
please list in terminal:
> sudo fdisk -l

---

### Post by jnorthr on 2007-07-10
Don't panic. You will rarely loose your windows partition. It may be invisible as the MBR is played with during ubuntu install. At worst you will need to use something like super grub or other partition manager to rebuild your mbr.

---

### Post by nayana on 2007-07-10
oh, when i ran 'fdisk -l'  it gave me no output..but now when i run it as root it does gives an output

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/tracks, 729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot           Start            End             Blocks            Id         System
/dev/sda1  *                  1          6992             56163208+   83        Linux
/dev/sda2                 6993         7296               2441880       5         Extended
/dev/sda5                 6993         7296               2441848+   82        Linux swap / Solaris

---

### Post by renatoc8 on 2007-07-10
Hey, I don't see a ntfs Windows partition in your fdisk output. If you only have one hard drive, it looks like you overwrote your windows partition as is default in many Linux installers. If this is the case there is nothing you can do really.

Keep in mind, whenever you do anything that can potentially touch the partition table, make backups. I wish you luck and hope you didn't have any important files in the Windows partition, and welcome to the Ubuntu community! theres no real going back now :(

 -Renato

---

### Post by mjwhitfield on 2007-07-10
Aye it looks like windows is gone.  It's a shame that you've lost your files, but welcome to the community.  Ask lots of questions here to make sure you get everything working so you're happy with Ubuntu.

---

### Post by logos34 on 2007-07-10
> I followed the steps on the ubuntu site for dual boot and allowed the installer to **resize my partitions**. Any idea what happened? did the installer overwrite my MBR? when I do "df", or check fstab, i dont see any partitions other than /dev/sda1...have i lost all my data that was on my windows partition? is there anyway i can recover windows? I read in one thread about creating a rescue CD, is there anyway i can recover using the ubuntu installation CD?

.........

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/tracks, **729 cylinders**
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
**/dev/sda1 * 1 6992 56163208+ 83 Linux**
/dev/sda2 6993 7296 2441880 5 Extended
/dev/sda5 6993 **7296** 2441848+ 82 Linux swap / Solaris

Are you sure you didn't select the 'use entire disk' option (it's just below the 'resize' option)? Windows is gone, linux root and the extended partition with swap is taking up the entire hard disk.

You could try TestDisk to recover lost windows

---

### Post by nayana on 2007-07-10
hmmm that kinda sucks....but i guess its good that i had backups of all my data....

so can someone point out what i did wrong? I went through the automatic partitioning section of the installer and the ubuntu docs on dual boot seemed to indicate that everything will be taken care of when resizing the partitions, and that i wont loose my windows data....

thanks for all your help :)

---

### Post by nayana on 2007-07-10
> **logos34 said:**
> Are you sure you didn't select the 'use entire disk' option (it's just below the 'resize' option)? Windows is gone, linux root and the extended partition with swap is taking up the entire hard disk.

You could try TestDisk to recover lost windows

I only had two options when the partitioning step came (was installing 7.04)
1) Use the tool
2) Do it manually

when i selected 1, they didnt ask me for a size or anything...i also tried to see what options it gives me when I select 'manual', and it showed me the partition table with just one partition and there were no options to resize, only to add a new table completely, so i opted for the automatic step...

---

### Post by d_yat on 2007-07-10
hey nayana, just been googling in the web and found this

[http://www.linux.com/articles/56588](http://www.linux.com/articles/56588) " How to recover lost files after you accidentally wipe your hard drive"

a guy who lost all his files on his hard drive after partitioning it without backup basically.
dunno if it will work for you, but hope it does. ^_^
It would be 'somewhat' annoying to have lost all your stuff.

---

### Post by louieb on 2007-07-10
> **logos34 said:**
> Are you sure you didn't select the 'use entire disk' option (it's just below the 'resize' option)? Windows is gone...
That would  do exactly what you described.  Glad you had a backup. Just for future reference. Heres a couple of handy tools to keep around when messing with you computer. [SystemRescueCd]("http://www.sysresccd.org/Main_Page") [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/")

---

### Post by renatoc8 on 2007-07-10
> **nayana said:**
> hmmm that kinda sucks....but i guess its good that i had backups of all my data....

so can someone point out what i did wrong? I went through the automatic partitioning section of the installer and the ubuntu docs on dual boot seemed to indicate that everything will be taken care of when resizing the partitions, and that i wont loose my windows data....

thanks for all your help :)
That's where you went wrong, you went though the automatic partitioner. Even if it said EXACTLY what it was doing, I would never let anything automatic touch my partition table. Always do this type of change by hand.

 -Renato

---

### Post by luper on 2007-09-12
I posted in another help thread but I did fdisk (sda instead of hda)

I have 4 parts, ntfs, linux, backup(ibm restore partition), and swap

I am getting the mount erro when trying to start windows and my linux sound doesn't work. (i think it did at first but I'm not sure.. it is recognizing the sound card though and i checked volume levels)

Any help is appreciated.
-luper

ADD: I am going to use the IBM restore and get my xp first (b/c i aint got no discs! lmao)... then I'm going to MANUALLY do the partitioning during ubuntu setup... Thatseems best choice

ADD2: Well damn... the image file was corrupt or something it said... that SUCKS. Bootlegged xp here i come.

---

### Post by p_quarles on 2007-09-12
@nayana: Did you install this over Windows Vista, by any chance? For older versions of Windows, the live CD is good at giving you the option of resizing the disk automatically, but with Vista (for whatever reason), it has trouble recognizing the existing filesystem. 

If that's the case, there's an easy solution: use Vista's partition manager to create free space on the disk. Then, during the Ubuntu installation, you can tell it to create the new partitions on the free space.

---

### Post by luper on 2007-09-12
no.. this is a laptop I bought recently (older one). It has Win xp pro on it. Now though its trashed or something... I'll just obtain a copy of xp, format the whole shibang, then git r done from there.


I am wanting to use VirtualBox (b/c i just want to run office 2007 for school)... CAN I just install ubuntu then when I add a virtual machine, install xp from there? OR do I ahve to install it first. Thanks.
-luper

Ok yeah... im going to install ubuntu then add xp as virtual. Thanks for help. I actually have two laptops now (this one battery is better than my other 7510gx )... so thanks for help!!!

-luper

---

