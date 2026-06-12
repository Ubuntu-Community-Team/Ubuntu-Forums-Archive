---
title: "Installing 11.04 on MacBook Pro, Can't See Partition"
date: 2011-05-03
forum: Apple Hardware Users
---

### Post by jasonmac53 on 2011-05-03
I've been trying to install 11.04 on my MacBook Pro5,2, (already have Mac OS X Snow Leopard and Windows 7 installed) but every time I get to screen where it asks me to install, the installation GUI doesn't see my partitions. The strange thing is that if I run sudo fdisk -lu /dev/sda I get:


Disk /dev/sda: 160.0 GB, 160041885696
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32104075

   Device      Boot            Start                   End                Blocks      Id      System
/dev/sda1                           1             409639            204819+     ee     GPT
/dev/sda2      *         409640        166425271         83007816      af      HFS / HFS+
/dev/sda3           166688768        254389274       43850253+      7      HPFS/NTFS
/dev/sda4           254390272        312580095        29094912      83      Linux


Seems like everything is fine, no sectors are overlapping, and fdisk definitely recognizes the partition. But when I run the graphical install, I get a menu that says:


Device             Type    Mount point    Format?     Size              Used
/dev/sda
  free space                                                        0 MB
  /dev/sda1      efi                                              209 MB         209 MB
  /dev/sda2     hfs+                                           85000 MB      76954 MB
/dev/sdb
...


There's no option to choose /dev/sda4!! (or even /dev/sda3, my Windows partition)

If it also helps to know, /dev/sda is an Intel x25-M SSD, and I also have another internal HDD (using an OptiBay), so I'm running the install from an external DVD drive.

---

### Post by srs5694 on 2011-05-03
First, in the future, please enclose text-mode output between  [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. This  helps legibility. I sometimes skip posts that aren't formatted in this  way; it's just too tedious to read otherwise. Here's your fdisk output  done in this style:

```
# fdisk -lu /dev/sdb

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00022117

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63      192779       96358+  83  Linux
/dev/sdb2         1012095   625137344   312062625   8e  Linux LVM
/dev/sdb3          192780     1012094      409657+  82  Linux swap / Solaris
```

Note how the columns line up? That's much easier to read to extract the columnar data.

More important, does your fdisk output include a warning like this:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk
doesn't support GPT. Use GNU Parted.

```If it doesn't, then there's something very seriously wrong with your partition table, since Macs normally use GPT disks, and fdisk normally detects the GPT data structures and squawks if they're missing.

In any event, to figure out what's going on, I recommend you install [GPT fdisk (gdisk)]("http://www.rodsbooks.com/gdisk/"). You should be able to do a "sudo apt-get install gdisk" in the 11.04 installer in "live CD" mode; or download the version for whatever Linux distribution you've got installed from OBS, as described in the OBS section of [this page.]("http://www.rodsbooks.com/gdisk/download.html") With this package installed, type:

```

sudo gdisk -l /dev/sda
sudo gdisk -l /dev/sdb

```If you're asked whether to use MBR or GPT data, run the program twice, and respond once each way. Post the *complete* results back here.

---

### Post by jasonmac53 on 2011-05-03
Yes, I did get the "GPT (GUID Partition Table) detected on '/dev/sda'!" warning.

Here is the result of sudo gdisk -l /dev/sda:

```


GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 312581808 sectors, 149.1 GiB
Disk identifier (GUID): C478108C-9661-4180-B22B-1A18CC61A043
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312581774
Total free space is 266178 sectors (130.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       166425271   79.2 GiB    AF00  Mac OS X


   3       166688768       254389274   41.8 GiB    0700  BOOTCAMP
   4       254390272       312580095   27.7 GiB    0700  

```

Here is sudo gdisk -l /dev/sdb with MBR chosen:

```


GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: Disk /dev/sdb: 976773168 sectors, 465.8 GiB
Disk identifier (GUID): D647A4F0-6209-0F57-E51E-D6B9F36ADB05
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Total free space is 933861 sectors (456.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2          409640       976248879   465.3 GiB   AF00  Apple HFS/HFS+

```

and here is sudo gdisk -l /dev/sdb with GPT chosen:
```


GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: Using GPT and creating fresh protective MBR.
Disk /dev/sdb: 976773168 sectors, 465.8 GiB
Disk identifier (GUID): 448F2655-2040-422E-8612-C21BF3D183B6
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Total free space is 933861 sectors (456.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2          409640       976248879   465.3 GiB   AF00  Seagate

```

---

### Post by srs5694 on 2011-05-04
I have three observations/suggestions.

First, your output shows you're using gdisk 0.5.1, which is woefully out of date -- the current version is 0.7.1. Although I don't recall any bugs in 0.5.1 that will affect what I'm about to suggest you do, I'm pretty sure the current version has better error-detecting and correction code, so you should upgrade. Ubuntu 11.04 ships with gdisk 0.6.13 or 0.6.14, IIRC, which is reasonably current, so you can use gdisk from that installer; or you can download and install 0.7.0 from [its Sourceforge page](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.0/gdisk-binaries/) or 0.7.1 from the OpenSUSE Build Service, as described [here.](http://www.rodsbooks.com/gdisk/download.html) (0.7.1 uses new libraries that vary a lot from one distribution or version to another, so as of 0.7.1, you've got to match what you install to your distribution and version; whereas with earlier versions, you could often install a package built on a significantly different distribution or version).

Second, and most clearly, your /dev/sdb is a bit messed up, since you've got both GPT and MBR partition tables defined, but not in a hybrid MBR setup. This type of problem is known to confuse libparted and tools based on it, such as GParted and the partitioner in the Ubuntu installer. Thus, I recommend you fix this. The good news is that the GPT and MBR sides are entirely consistent with one another -- they both define the same partition, which is one big HFS+ partition, so I'm guessing it's an OS X disk. If so, I recommend you do this to fix it:


[list=1]
[*]Boot Linux and, if necessary, re-install gdisk.
[*]Open a Terminal window.
[*]Type "sudo gdisk /dev/sdb". The program should launch and ask you whether to use the GPT or MBR data, as it did when you used gdisk to view the partition tables.
[*]Select option 2, GPT. (Option 1 would work as well.)
[*]Type "p" to view the partition table and verify that it's showing the correct data, as in your post.
[*]Type "v" to verify the integrity of the partition data. If gdisk complains of any inconsistencies, type "q" and post back the results; otherwise, go ahead....
[*]Type "w" to save your changes to disk. You'll be asked to verify this action.
[/list]


There's a small chance that fixing /dev/sdb will also fix the Ubuntu installer's inability to see beyond /dev/sda2 on your other disk; however, the two issues may be unrelated. Thus, my third point: If the preceding doesn't help, I have another question: In your gdisk output for /dev/sda, there are two blank lines between /dev/sda2 and /dev/sda3. Are those lines present in the actual output, or did they get added accidentally when you cut-and-pasted the output into your post? If those blank lines are present in the gdisk output, I find it suggestive that this break occurs at the same place as the installer's "break" in its ability to see the partitions on the disk. Thus, I recommend you try the following:


[list=1]
[*]As above, prepare to run gdisk.
[*]Type "sudo gdisk /dev/sda" to launch gdisk on /dev/sda.
[*]Type "p" to view the partition table to be sure you're working on the correct disk.
[*]Type "v" to verify the data structures. If gdisk reports any problems, please type "q" to quit, skip the remaining steps, and report the gdisk output back to me. If this happens, I may ask you for a copy of your GPT data, which you can acquire (before exiting from gdisk) by typing "b" and entering a filename. Put the file on permanent storage so you can deliver it to me for analysis.
[*]If "v" doesn't report any problems, type "c" to change a partition name and change the name of partition 2. You can give it the same "Mac OS X" name it's got now, if you like.
[*]Type "p" to view the partition table again. If the two-line gap between partitions 2 and 3 still exists, save the backup partition table and quit from the program without saving your changes. If the gap is gone, though, type "w" to save the changes.
[/list]


My hypothesis is that newline characters have somehow found their way into partition #2's name field, and this is causing Ubuntu's installer to flake out and ignore the partitions after that one on the disk. If so, setting the partition's name field should fix the problem. If not, though, there's probably something else very peculiar about that partition table, which may require expert analysis. (That is, by me -- I don't recall if I mentioned it in this thread, but I'm the author of gdisk.)

---

### Post by jasonmac53 on 2011-05-04
Wow, so using gdisk to change the partition name fixed the issue! I ran gdisk again and it no longer printed line breaks, so I guess that my partition name somehow had newline characters at the end. Also, for future reference, I don't believe that gdisk comes standard on Ubuntu. Thanks so much for your help!

---

### Post by srs5694 on 2011-05-04
I'm glad that fixed it. FWIW, gdisk *does* come with Ubuntu, in the sense that it's in the repositories, but it's not installed by default -- at least, not on any of the installations I've ever done.

---

