---
title: "Can I merge partitions on MacBook?"
date: 2008-07-09
forum: Apple Hardware Users
---

### Post by JoJerome on 2008-07-09
MacBook SantaRosa 3.1.
160g HD.
rEFIt installed and working beautifully.

Used BootCamp to partition as per the instructions in this Forum's Apple Users FAQ: 80g for OSX, 80g for Gusty. Took several tries, but Gusty installed.

However, didn't get much further than that. Every attempt to update using Adept Installer crashed. Soon, Gusty stopped booting at all. I'd get the logon screen, I'd logon, the screen flickers a few times, then I get the logon screen again.

So, am now trying to install Hardy from a CD. However; somewhere in there my Kubuntu partition seems to have split in half. Specifically, when I try to install Hardy from CD, I go to manual partition, and I get the following overview of my drive:

<code>
SCSI3 (0,0,0) (sda)  -  160.0GB ATA ST9160821AS
                      3.1kB       Free Space
           #1 209.7MB B    Fat32 EFI System P
           #2  79.36GB       hfs+        Customer
                134.2MB        FREE SPACE
           #3   39.5GB        ext3        untitled
                   38.5GB        FREE SPACE
           #4      2.2GB B     ext3
           #5  168.2MB    F  swap           swap
</code>


I tried going into BootCamp to fix the partitions, but the error I get is:
<code>
The Startup Disk cannot be partitioned or restored to a single partition.
The Startup Disk must be formated as a single Mac OS extended (journaled) volume or already partitioned by BootCamp for installing Windows.
</code>

So ... Help! Is it possible to merge those two 39.5g/38.5g partitions? How?

Thanks in advance...

- Jo

---

### Post by damis648 on 2008-07-09
Use partedmagic (the livecd). Just boot your mac up with that CD and repartition to your heart's content.

---

### Post by JoJerome on 2008-07-09
> **damis648 said:**
> Use partedmagic (the livecd). Just boot your mac up with that CD and repartition to your heart's content.

partedmagic - is that part of the Hardy install cd or is that a different program I'd be downloading?

Thanks!

- Jo

---

### Post by damis648 on 2008-07-09
> **JoJerome said:**
> partedmagic - is that part of the Hardy install cd or is that a different program I'd be downloading?

Thanks!

- Jo

This would be a separate ISO.

---

### Post by Ptero-4 on 2008-07-09
It's another liveCD distro.

---

### Post by cyberdork33 on 2008-07-10
actually you can just boot the Ubuntu LiveCD, and start the partition editor (in the system > admin menu).

If you are going to reinstall anyway, just delete the two ext3 partitions and the swap space so all you have is free space at the end. then start the installer and choose to install to the largest free space. You will likely run into the installer bug, so keep this handy too:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by callumbaillie on 2009-07-23
Hi
To merge a windows partition that has already had the windows os removed. Goto on your mac partition utilities >> Disk Rtility  then click the windows partition. Click Erase tab and select "MS-DOS(FAT)" and name it untitled.

Then goto Bootcamp and the installer will allow you to erase partition and merge it with exsisting Mac osX Partition.

WARNING: ALWAYS MAKE A BACKUP BEFORE MERGING, FORMATING OR INSTALLING AN OS ON BOTH SIDES OF THE PARTITION.

---

