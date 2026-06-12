---
title: "Dual Boot 7.04/XP with a shared ext3 part questions"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Mukaeutsu on 2007-09-06
Finally, moving to Ubuntu! Just new to LINUX as a whole, and have many questions!

I have recently slicked my 80GB drive and installed the following partitions:
part 1 200MB [ /boot ] (primary) Ext3
part 2 ~12GB WinXP Home x86 (primary) NTFS*
part 3 8GB Ubuntu 7.04 AMD64 [ / ] (primary) Ext3
part 4 56GB common storage [ /hda5 ] (logical) Ext3 
part 5 3GB swap (logical)                                    **in theory, part 4/5 are in the extended part**
*the NTFS part is just an empty space as of now, as if i have to reconfig this, xp takes too long to install to do it multiple times*

My questions are mainly regarding the Storage Ext3 partition:

1) i had read a guide suggesting [/hda5] as a mount point for this, so i followed that, but cant seem to find that drive (i found hda5 but only Lost and Found was in it and said i lacked access permission (though i am a SUPER))

2) using ext2fsd for windows, i understand i will have r/w capabilities on ext2/ext3, but will i be able to install World of Warcraft in my storage part, and have access through XP and Ubuntu AMD64+Wine to play it?

3)any other suggestions as to additional partitions (some info said have a big /usr small /home, others the opposite) i am unfamiliar with exactly what the different /folders are in ubuntu and have searched through wikis only to be left without answer =\

Thanks Everyone for all of your input.
Mukaeutsu

---

### Post by rsambuca on 2007-09-06
The problem with asking for advise on partitioning strategies is that 10 people will give you 10 different answers!  In any event, here is my advice:

1. Skip the /boot partition.  You don't really need to worry with a separate partition for this unless you will be installing on external drives.

2.  Install XP first, so that when you install ubuntu after that the grub loader will detect XP and give you the option of which OS to use when you boot up.

3.  I don't know why, but I would put the ubuntu root partition and the swap inside of the extended partition, and keep the storage/media partition separate.

4.  You will not be able to use WoW from both OS's.

5.  You will not need 3GB for swap unless you are running some very heavy programs.  with 1GB ram, 1 or 2GB swap will be plenty.

---

### Post by Mukaeutsu on 2007-09-06
okay, thanks for that input, i may actually follow up on that

as you were saying, WoW would not be accessible from both, so i would need to install WoW onto WinXP, then Wine+ WoW onto Ubuntu separately?

also, with an 80GB HDD, can you assist me with a layout schematic for the disk (I have more programs than storage based files, so i may need to increase the 2 OS's partitions to compensate

Thanks very much,
Muk

---

### Post by toidi on 2007-09-06
You will be able to use wow on both ubuntu and windows.  I do it here and have no problems.

Not sure if windows will be able to use ext3 though, this is how I got wow to work in both.

Installed xp and then installed wow to C:\wow for easy access.

Installed ubuntu onto a second partition.

Made sure I had read/write/exec permission on my ntfs partition.  Created a shortcut on my ubuntu desktop to "wine /media/hda1/wow/WoW.exe

Worked a treat.

---

### Post by rsambuca on 2007-09-06
> **toidi said:**
> You will be able to use wow on both ubuntu and windows.  I do it here and have no problems.

Not sure if windows will be able to use ext3 though, this is how I got wow to work in both.

Installed xp and then installed wow to C:\wow for easy access.

Installed ubuntu onto a second partition.

Made sure I had read/write/exec permission on my ntfs partition.  Created a shortcut on my ubuntu desktop to "wine /media/hda1/wow/WoW.exe

Worked a treat.I stand corrected!

---

### Post by Mukaeutsu on 2007-09-06
so, use ntfs3g for ubuntu to see windows, rather than the other way around?
would i set up my shared storage under NTFS as well then, or use ext3fsd so windows can see ext2/3 (if i can do the latter for the storage i would prefer that, ext3 seems to be better built than NTFS

---

### Post by Sef on 2007-09-06
> [http://www.fs-driver.org/](http://www.fs-driver.org/)

To access ext3 from XP, read '[Ext2 Installable File System For Windows]("http://www.fs-driver.org/").'

---

### Post by toidi on 2007-09-06
I am still new to this whole linux thing.  Getting ubuntu to see ntfs was what I did.

```
sudo apt-get install ntfs-config
```

Grabs ntfs3g and then you can gui control of your ntfs drive.
Not sure about the other way around when it comes to storage drives as I have only booted into windows once since installing ubuntu.

> **rsambuca said:**
> I stand corrected!
Only took me two weeks and 3 different 7gig WoW folders to figure that one out ;)

---

### Post by Mukaeutsu on 2007-09-06
again, thanks all for you help... the last thing i NEED to find out, is if programs installed on the storage area can be used

it seems that through the 'shortcut' route, linux w/ NTFS r/w will be able to run a program from there, but can anyone find out/ share if windows can actually run a program installed onto the ext3 drive
from what i gathered from 'Ext2 Installable File System For Windows.' link above, it sounded more like windows can run a program that uses some info from said ext3, but can the entire source be ext3

that really is the deciding factor on which file sys i use
again, thanks a ton everyone, you all have been very helpful in my delema

Muk

---

