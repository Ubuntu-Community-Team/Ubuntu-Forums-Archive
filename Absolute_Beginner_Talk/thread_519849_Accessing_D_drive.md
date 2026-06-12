---
title: "Accessing D drive"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by kyalee on 2007-08-07
I have a desktop computer with two internal hard drives, one ~15 GB (C drive) and one ~35GB (D drive). I just loaded Ubuntu (feisty fawn 7.04) today. It loaded fine, but I can't find my D drive. In Windows when I went to My Computer, I saw both the C drive and the D drive listed. When I go to Computer, I see "file system" along with the floppy drive, and both CD drives, but that's it. Does anyone know how I can display both my C drive and my D drive the way it did in Windows?

I'm sorry this is so non-technical. I'm really, really new at this and right now just hoping I didn't completely screw things up.

---

### Post by Rocket2DMn on 2007-08-07
In linux you don't see C:\ or D:\ - drives are not referenced by a drive letter.  They are "mounted" at a specific location within your filesystem.  So for example, to view my windows partition, i go to the folder /media/windows/
Please post the output of the following commands from terminal:
```
sudo fdisk -l

cat /etc/fstab
``` With that we can help you get your second hard drive to show.

Here is a good do it yourself guide: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by kyalee on 2007-08-07
Okay, when I put in "sudo fdisk -l"

I got: 

> Disk /dev/hda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7126    57239563+  83  Linux
/dev/hda2            7127        7301     1405687+   5  Extended
/dev/hda5            7127        7301     1405656   82  Linux swap / Solaris

When I put in "cat /etc/fstab"

I got:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5b126daf-dd35-4747-b6f2-4e45c04cfa9c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=ae9d1f3f-2f37-4912-8ddd-8bb41cbef3f0 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Goot thing? Bad thing? :confused:

---

### Post by Inxsible on 2007-08-07
I think you over wrote Windows :(.... Did you mean you have two physically different hard drives or just 2 partitions on one drive?

i ask because you said..you had a 15GB and a 35GB drive, whereas your fdisk only shows 1 60GB drive

What option did you choose while installing Ubuntu ? 
Guided partitioning or Manual partitioning ?

---

### Post by Rocket2DMn on 2007-08-07
Eh, he said he had 2 hard drives.  You didn't by chance mean that you had 2 partitions on 1 hard drive did you?  The output of the first command only detects 1 physical hard disk inside your computer.
If you had the drive partitioned, then when you installed Ubuntu, it appears you overwrote the whole drive including Windows if you still had that.

---

### Post by vexorian on 2007-08-07
hi

Take synaptic and get this package "ntfs-config"

Install it, then you'll find ntfs-config under applications/system (top menu)

Run that program, it will ask your password and will then detect (and setup) your ntfs partitions, you may try to check write access if you want, but I would not recommend to do it , instead I just enable write access for occasional writing but I never leave it enabled before booting windows.

If things go well you will be able to see your old hard drive partitions in the gnome desktop.

---

### Post by kyalee on 2007-08-07
I didn't do a dual boot, if that's what you mean. But shouldn't I still be able to get to the D drive? I'm not trying to access the old Windows OS, or even the files that were there. (I was hoping I'd still have them--that Linux would load on the C drive and leave the D drive alone, the way XP seemed to be contained on the C drive and leave the D drive for other files; but I knew I was taking a chance on losing the files and accepted that. The important files are backed up anyway.) I'm just confused about the way it's displaying, I guess.

For example, in Windows (sorry, I know people probably hate it when people whine "but windows did this!" but it's the only frame of reference I have right now) when I right clicked and went to properties, it would tell me how much free space was left on the disc. When I right click and go to properties of Filesystem, it tells me the the size is unknown.

I guess I just liked the way XP plainly displayed the two drives and I knew how much space was left on each and I'm wondering how I can get the same information with Linux.

---

### Post by Inxsible on 2007-08-07
> **vexorian said:**
> hi

Take synaptic and get this package "ntfs-config"

Install it, then you'll find ntfs-config under applications/system (top menu)

Run that program, it will ask your password and will then detect (and setup) your ntfs partitions, you may try to check write access if you want, but I would not recommend to do it , instead I just enable write access for occasional writing but I never leave it enabled before booting windows.

If things go well you will be able to see your old hard drive partitions in the gnome desktop. You are a little late on the boat my friend. :)

 He/She has probably nuked Windows while installing Ubuntu :(

EDIT : Scratch that...he/she did it on purpose :)

---

### Post by kyalee on 2007-08-07
> **Inxsible said:**
> I think you over wrote Windows :(.... Did you mean you have two physically different hard drives or just 2 partitions on one drive?

i ask because you said..you had a 15GB and a 35GB drive, whereas your fdisk only shows 1 60GB drive

What option did you choose while installing Ubuntu ? 
Guided partitioning or Manual partitioning ?

As far as I know, it's two physically separate drives (never cracked the case and saw for myself, but that's what they told me *g*). I'm confused too about why it's showing one 60GB harddrive when XP always showed me two. Weird.

I used guided partitioning--use entire disc when I installed.

---

### Post by kyalee on 2007-08-07
> **Rocket2DMn said:**
> Eh, he said he had 2 hard drives.  You didn't by chance mean that you had 2 partitions on 1 hard drive did you?  The output of the first command only detects 1 physical hard disk inside your computer.
If you had the drive partitioned, then when you installed Ubuntu, it appears you overwrote the whole drive including Windows if you still had that.

As far as I know, it's two physical hard drives, not a partition, but I'm only basing that on the way it's always displayed in XP. I'm confused myself as to why it's suddenly telling me I have 1 6o GB hard drive.

---

### Post by Inxsible on 2007-08-07
> I guess I just liked the way XP plainly displayed the two drives and I knew how much space was left on each and I'm wondering how I can get the same information with Linux. you can get that information using this command in the terminal
```
df -h
```

---

### Post by Inxsible on 2007-08-07
>  I used guided partitioning--use entire disc when I installed That would be why all your Windows drives and files are gone !

and no I dont think you have two physically separate drives. I guess when you got the Windows machine originally, it was pre installed with Windows and had the partitions there already.

---

### Post by dca on 2007-08-07
One was data partition, other recovery partition or in newer systems:  one is OS partition, other is data partition...???

---

### Post by kyalee on 2007-08-07
> **Inxsible said:**
> That would be why all your Windows drives and files are gone !

and no I dont think you have two physically separate drives. I guess when you got the Windows machine originally, it was pre installed with Windows and had the partitions there already.

So I did write over the D drive (or what I thought of as the D drive). Feh. Oh well. Thank goodness for backups. ;) All I've lost is a crap load of music that I can mostly get back and way more Stargate pictures than any one person needs anyway. *g*

And I never had two physical drives? News to me!

Strangely, I tried to go a guided install with a partition, but I couldn't get it to work which is why I went with the use entire disk option. I assumed partitioning wasn't working because there were two physical disks in there, but if there never were, I wonder why it didn't work.

Well, I guess that rules out accessing those files then. Thanks for the help!

---

