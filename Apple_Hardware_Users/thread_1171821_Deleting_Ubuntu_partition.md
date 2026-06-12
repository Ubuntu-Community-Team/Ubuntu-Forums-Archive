---
title: "Deleting Ubuntu partition"
date: 2009-05-27
forum: Apple Hardware Users
---

### Post by hollyjester on 2009-05-27
Okay, big problem. I booted into OS X, and opened up boot camp. Then I restored the internal hard drive on my Macbook 4,1. After that, I deleted the efi folder so rEFIt wouldn't load up at the start. My OS X says it has a 140 GB capacity. I am guessing the Ubuntu partition still exists, but I don't know how to delete it, and nothing shows up in Disk Utility.

---

### Post by pastalavista on 2009-05-27
You can boot from the Ubuntu live CD and use partition editor in the system > administration menu. Delete the ubuntu partition and expand the osx partition to fill the empty space.

---

### Post by hollyjester on 2009-05-28
Okay, I will try that. I guess it means I have to go do that again.

---

### Post by hollyjester on 2009-06-23
I tried GParted, but the partition won't show up, even though it does show up as Legacy OS using rEFIt.

---

### Post by hollyjester on 2010-04-13
Some please help! This is problem that is giving a lot of trouble and worry, as I have a 100 GB less of storage space. I need that space! Help please!

---

### Post by pastalavista on 2010-04-13
I can't understand why the partition didn't show up in gparted. Boot the live CD again open a terminal and post the output of ```
sudo fdisk -l
``` Why can't you remove it with Boot Camp?

---

### Post by srs5694 on 2010-04-14
OS X uses GPT by default, so Linux's fdisk, which is MBR-only, won't be very useful. There's an OS X tool called "gpt" that will provide similar information for GPT, but I'm not very familiar with it. You could try my [GPT fdisk (gdisk)]("http://www.rodsbooks.com/gdisk/") (versions for Linux and OS X are available), as in:

```

sudo gdisk -l /dev/disk0

```This works from OS X; from Linux, change "/dev/disk0" to "/dev/sda". This will show you what your partitions are. You can use GPT fdisk to delete the Linux partition, assuming you can unambiguously identify it. In theory, you should then be able to resize the OS X partition with Disk Utility or GParted.

It's conceivable you've got something weird going on with a [hybrid MBR]("http://www.rodsbooks.com/gdisk/hybrid.html") configuration that's complicating matters. If so, the gdisk output will at least identify the fact that you've got a hybrid MBR; it will report "MBR: hybrid" as part of its "partition scan" output. If you're trying to set up an OS X-only configuration, a hybrid MBR can cause nothing but trouble, so if you've got one, you should eliminate it. This can be done with the 'n' option on the GPT fdisk experts' menu. OTOH, if you want to dual-boot OS X and Windows, a hybrid MBR is helpful (maybe even necessary; I'm not sure if Boot Camp requires it).

Edit: Oh wait, I think I see pastalavista's point; Linux fdisk will reveal whether a hybrid MBR is in use. It's certainly useful for that.

---

### Post by hollyjester on 2010-04-14
I tried your solution, and typed the following command into the terminal
> sudo gdisk -1 /dev/disk0

However, I got out:
> sudo: gdisk: command not found

---

### Post by srs5694 on 2010-04-14
Did you install the package? If so, it should be in /usr/sbin (in OS X), so you could try:

```

sudo /usr/sbin/gdisk -l /dev/disk0

```

If that doesn't work, it's not installed.

Also, it's "-l" (lowercase L), not "-1" (digit 1).

---

### Post by hollyjester on 2010-04-14
Are you sure it is in /usr/sbin? There is no such directory. I get the same message as before, command not found. Is there a place I can download it from?

---

### Post by hollyjester on 2010-04-14
Also, I confirmed a partition does exist. I turned on my Macbook, and held down ALT until I got the boot disk option. And there was a windows disk. When I clicked on it, I got the message "Missing operating system". So it is there, but Disk Utility or gParted won't recognize it.

---

### Post by hollyjester on 2010-04-14
I tried gpt fdisk. There is an EFI system. But that is 200 MB, not the 100GB I am missing. But I know it is there! See above reply.

---

### Post by srs5694 on 2010-04-14
> **hollyjester said:**
> Are you sure it is in /usr/sbin? There is no such directory. I get the same message as before, command not found. Is there a place I can download it from?

There's certainly a /usr/sbin directory on my OS X systems (I've run 10.5 and 10.6). I provided a link for the main GPT fdisk Web site earlier. You can download the package file from its [Sourceforge downloads page;](http://sourceforge.net/projects/gptfdisk/files/) as I posted before, you *do* need to install it (it's not a standard OS X utility).

---

### Post by srs5694 on 2010-04-14
> **hollyjester said:**
> I tried gpt fdisk. There is an EFI system. But that is 200 MB, not the 100GB I am missing. But I know it is there! See above reply.

If you've gotten it to run, please post the output of "sudo gdisk -l /dev/disk0", as I requested. I can't help you diagnose the problem without more precise data, as provided by GPT fdisk or a similar utility.

---

### Post by linuxopjemac on 2010-04-15
forget it..

---

### Post by hollyjester on 2010-04-15
Sorry, I misunderstood. Here are the details:
> 
GPT fdisk (gdisk) version 0.6.6

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/disk0: 312581808 sectors, 149.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00000231-561E-0000-8A51-0000FC5A0000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312581774
Partitions will be aligned on 8-sector boundaries
Total free space is 262157 sectors (128.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       312319623   148.7 GiB   AF00  Customer


---

### Post by srs5694 on 2010-04-15
According to that output, you have:


[list]
[*]A [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration
[*]An EFI system partition of 200 MiB (which is normal on this size of disk)
[*]A 148.7 GiB OS X partition called "Customer". (GPT fdisk doesn't look inside partitions, though, so I can't tell if it's got a proper OS X filesystem on it.)
[*]128 MiB of free space after the "Customer" partition. This is also normal on Mac disks.
[/list]


My suspicion is that the hybrid MBR contains invalid data that's confusing OS X. If so, and if the above description is what you intent to have on the system, you should convert it into a regular protective MBR:


[list=1]
[*]Launch GPT fdisk in interactive mode by typing "sudo gdisk /dev/disk0". You should see a prompt that reads "Command (? for help):".
[*]Type "p" to verify that you're using the same disk identified above. ("p" produces the same output as "gdisk -l" at a shell prompt.)
[*]Type "x" to enter expert mode. The command prompt will change.
[*]Type "n" to create a new protective MBR. The program won't display any data; it'll just give you a new command prompt.
[*]Optional: Type "o" to view the MBR partitions. You should see just one, of type 0xEE, sized to span the whole disk. You can also type "v" to perform a verify function, which will warn you of any problems.
[*]Type "w" to save your changes.
[/list]


With any luck your system should begin behaving more sanely at this point. If not, you may need to make adjustments to your rEFIt configuration; it could be referring to the old and now non-existent MBR partitions (I don't know much about rEFIt, though).

---

### Post by hollyjester on 2010-04-16
It didn't work. But now that I know more about MBR partitions, I think the hybrid partition messed up Boot Camp when it restored OS X to the whole drive. Thanks for your help. Hopefully someone comes along (maybe you) with a better solution.

---

### Post by srs5694 on 2010-04-16
I'd like to state my understanding of your current situation and ask some further questions:


[list]
[*]Your main problem is that OS X's Disk Utility says that the disk is entirely blank. A screen shot of Disk Utility, when showing this disk, might provide some clues that you've overlooked.
[*]It's unclear to me if OS X is installed on the problem disk, and if so whether it boots correctly. Please elaborate on how you're booting OS X.
[*]Please re-run the "gdisk -l /dev/disk0" command and check the status of the MBR detection; it should say "protective." The partitions should be as stated in your earlier post (an EFI System partition and a type-AF00 partition). If the MBR status is still "hybrid," then you did something wrong in the procedure I outlined (you probably forgot to use 'w' to save your changes, although it could have been something else).
[*]Do you need the data on the problem disk? If not, you can use the 'z' ("zap") option on the experts' menu of GPT fdisk to completely wipe out all GPT data, then repartition the disk using GPT fdisk, Disk Utility, or any other partitioning tool.
[/list]

---

### Post by hollyjester on 2010-04-17
Attached is a screenshot of disk utility.

According to Disk Utility, or any other partition tool, OS X fills up my whole disk (except for the EFI partition). The problem is that all partition editors say my disk has a max capacity of 160 GB. However, I had 250 GB. 90 GB were lost when boot camp restored my partitions to all OS X. I had initially used boot camp to create a partition, which I would then use for Ubuntu (just like in the documentation). My guess is that the MBR hybrid partition messed up boot camp when it was restoring it.

The only OS I have right now is OS X. My computer boots directly into OS X, and I got rid of rEFIt.

I do not know if this helps, but when I turn on my computer and I hold down the ALT/OPTION key (allows you to select the OS you want to boot into), instead of just saying OS X, it also says Windows. I never ran Windows on my laptop, but maybe this is the partition that I created in boot camp to use for Ubuntu. So maybe it never got deleted?

---

### Post by hollyjester on 2010-04-17
> **srs5694 said:**
> 
Please re-run the "gdisk -l /dev/disk0" command and check the status of the MBR detection; it should say "protective." The partitions should be as stated in your earlier post (an EFI System partition and a type-AF00 partition). If the MBR status is still "hybrid," then you did something wrong in the procedure I outlined (you probably forgot to use 'w' to save your changes, although it could have been something else).


It says protective under MBR now. Everything is exactly how you describe it should be.

> 
GPT fdisk (gdisk) version 0.6.6

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/disk0: 312581808 sectors, 149.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00000231-561E-0000-8A51-0000FC5A0000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312581774
Partitions will be aligned on 8-sector boundaries
Total free space is 262157 sectors (128.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       312319623   148.7 GiB   AF00  Customer


---

### Post by srs5694 on 2010-04-17
> **hollyjester said:**
> Attached is a screenshot of disk utility.

According to Disk Utility, or any other partition tool, OS X fills up my whole disk (except for the EFI partition).

Your screen shot is consistent with the GPT fdisk output (making allowances for interpretations of GB vs. GiB).

> The problem is that all partition editors say my disk has a max capacity of 160 GB. However, I had 250 GB. 90 GB were lost when boot camp restored my partitions to all OS X.

This makes very little sense. I'm the author of GPT fdisk, and the value it reports as the number of sectors (312,581,808 for your disk) is based on a low-level system call that reports the disk's true size, independent of any partitioning system in use. (Specifically, for OS X it uses the DKIOCGETBLOCKCOUNT ioctl() call; for Linux, it's BLKGETSIZE or BLKGETSIZE64.) Furthermore, your Disk Utility screen shot shows the model to be a Fujitsu MHY2160BH. A Web search turns up quite a few hits, all of which specify this as a 160GB drive. Even if something were modifying the disk's apparent size at a very low level, I find it hard to believe that they would change the drive's model number.

Are you sure you don't have another hard disk on the computer? It's entirely plausible that you could have a 160GB and a different 250GB drive, or perhaps a 160GB and an 80GB or 100GB unit, totaling close to 250GB.

If you're *absolutely positive* that the drive is really a 250GB model, then I don't have any explanation. I suggest in this case that you open the computer for a physical inspection to verify the drive's make and model number. If the EFI or some other very low-level tool is changing the drive's model number and size, then that's a new twist to me, and you'll certainly need the mismatched visual inspection and data from disk identification software to get anywhere with Apple's tech support.

---

### Post by hollyjester on 2010-04-17
I am positive it is 250 GB. To my knowledge there is only one drive installed, unless Apple has some weird configuration with two drives. I guess I will take it to Apple, and have the tech support look inside.

Thanks for all your help though. Even if I didn't fix my drive, I know a lot more about partitions now! :)

---

