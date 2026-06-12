---
title: "Grub2 floating around..."
date: 2011-07-24
forum: Apple Hardware Users
---

### Post by madtowneast on 2011-07-24
Hi all,

I had to install Fedora instead of Ubuntu, because of a weird dependency in one of the codes I am running. Now I booted into the fedora CD and basically just formatted the ubuntu partitions and created a new partition table for the linux side of my MBP. I had Fedora installed before, so I now it works. Anyhow, after installing fedora I got the prompt:

```
error: file not found
grub rescue>
```

Now this seems to be a grub2 prompt. Can anybody help me with finding grub2? I am getting very confused as where it could be hiding after formatting the disks multiple times.

Thanks for any advice in advance.

---

### Post by drs305 on 2011-07-24
It's possible Grub 2 is still lurking in the MBR of the drive booted first and is trying (and failing) to find the non-existent Grub files. 

Have you installed your new bootloader (Grub legacy) to the MBR of your boot device?

Running the boot info script from an Ubuntu LiveCD or other Linux OS and posting the contents of RESULTS.txt may show us what's happening. (Click the "BIS" link in my signature line.)

---

### Post by madtowneast on 2011-07-24
Here is the result.txt. GRUB2 is on the EFI partition... now how do i get that off. Should i maybe install legacy grub on sda1 instead of sda3

---

### Post by drs305 on 2011-07-25
I'm not familiar enough with EFI and GPT to provide advice but I'll bump the thread as there are those who regularly read grub threads that can provide the solution.

---

### Post by srs5694 on 2011-07-25
I think that drs305's initial analysis is basically correct, although there are significant wrinkles because this is a Mac. The Boot Info Script reports that GRUB 2 is present in the MBR of the disk, but there's no mention of a grub.cfg (GRUB 2 configuration) file. You *do* have GRUB Legacy in the boot sector of /dev/sda3, and it appears to be configured correctly.

Do you use [rEFIt](http://refit.sourceforge.net/) on this computer? If so, I'd expect that it would detect the GRUB Legacy on the Linux partition and give you a boot option for it (but see below concerning partition types). If you're not using rEFIt, installing it might be the simplest solution.

If you're already using rEFIt and it's not giving you an option that boots to GRUB Legacy, then my guess is that the problem is related to the incorrect partition type code set on your Fedora partition (/dev/sda3). According to Boot Info Script, it's flagged as an EFI System Partition, but this is incorrect. You can fix this in GParted or parted by removing the "boot flag" from the partition, or in gdisk by changing the type code from EF00 to 0700 (or 8300 if you use gdisk 0.7.2, the latest; but I'm not sure if rEFIt will work with this code, which is new).

If none of the above helps, then I'd suggest re-installing GRUB Legacy to the MBR on the disk. There may be an option in the Fedora installer to do this; or you could use [Super GRUB Disk](http://www.supergrubdisk.org) (use Super GRUB Disk, not Super GRUB 2 Disk!) to boot into your Fedora system and re-install GRUB from there, as in "grub-install /dev/sda" as root.

An entirely different option would be to ditch the old-style BIOS booting and boot using EFI mode by installing an EFI-capable boot loader. [This page](https://help.ubuntu.com/community/UEFIBooting) describes how to compile and install GRUB 2 to boot in EFI mode; or you could give [ELILO](http://elilo.sourceforge.net) a try (although I've had little success with it on my Mac Mini). Fedora includes a version of GRUB Legacy that's been hacked to include EFI support, but I don't recall offhand precisely how it's set up by default. You could use an emergency disk to check for files in the Fedora /boot/efi directory. If there are files there, try copying them to your EFI System Partition (ESP; /dev/sda1) and see if rEFIt gives you a new boot option.

---

### Post by drs305 on 2011-07-25
Thanks for jumping in here *srs5694*

---

### Post by madtowneast on 2011-07-25
Thanks for the reply. Really appreciate it.

> **srs5694 said:**
> I think that drs305's initial analysis is basically correct, although there are significant wrinkles because this is a Mac. The Boot Info Script reports that GRUB 2 is present in the MBR of the disk, but there's no mention of a grub.cfg (GRUB 2 configuration) file. You *do* have GRUB Legacy in the boot sector of /dev/sda3, and it appears to be configured correctly.

Do you use [rEFIt](http://refit.sourceforge.net/) on this computer? If so, I'd expect that it would detect the GRUB Legacy on the Linux partition and give you a boot option for it (but see below concerning partition types). If you're not using rEFIt, installing it might be the simplest solution.

Tried that already. It gives me 2 linux boot options. Either produces the same error. Kind of odd..

> **srs5694 said:**
> If you're already using rEFIt and it's not giving you an option that boots to GRUB Legacy, then my guess is that the problem is related to the incorrect partition type code set on your Fedora partition (/dev/sda3). According to Boot Info Script, it's flagged as an EFI System Partition, but this is incorrect. You can fix this in GParted or parted by removing the "boot flag" from the partition, or in gdisk by changing the type code from EF00 to 0700 (or 8300 if you use gdisk 0.7.2, the latest; but I'm not sure if rEFIt will work with this code, which is new).

I just loaded the fedora live CD and found the option. To what should I change the type? There is not flag set according to fedora at least. 

EDIT:

I unset the boot flag and the set the Linux to a MBR map instead of EFI partition map. I tried to install grub using the Fedora disk, but it just gave me error saying that there is no bios driver installed. I might try to reinstall FEdora with teh bootloader being installed on sda1 instead of with Fedora on sda3. Is Rescatux a good option instead of SGD?

---

### Post by srs5694 on 2011-07-25
> **madtowneast]I just loaded the fedora live CD and found the option. To what should I  change the type? There is not flag set according to fedora at least.[/quote]

I'm not sure exactly what program or options you're seeing in the Fedora installer. I recommend you boot with [System Rescue CD](http://www.sysresccd.org) or [Parted Magic](http://partedmagic.com) and use GParted, parted, or gdisk, as described in my earlier post.

[QUOTE=madtowneast said:**
> I unset the boot flag and the set the Linux to a MBR map instead of EFI partition map.

Please clarify what you mean by this. What tool did you use and precisely what did you do with it? Some possible interpretations of what you might mean by this are *extremely* dangerous, so I'd really like to understand what you've actually done before advising you further. It might be good for you to post another Boot Info Script output, or the output of "sudo parted /dev/sda print" or "sudo gdisk -l /dev/sda" so we can see the current state of your partition table, if you've been making changes to it.

> I tried to install grub using the Fedora disk, but it just gave me error saying that there is no bios driver installed.

When reporting errors from programs it's imperative that you give a *verbatim* copy of the error message. If text-mode, copy-and-paste the error to this forum. If it's more than a few words, and especially if it contains formatted text, post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility. If it's a GUI program, post a screen shot. I've never heard of a "no bios driver installed" GRUB message, and I'm not entirely sure what that would mean, so I suspect you may have subtly altered the message in relaying it.

> I might try to reinstall FEdora with teh bootloader being installed on sda1 instead of with Fedora on sda3. Is Rescatux a good option instead of SGD?

I've never used Rescatux, so I can't comment on it.

Installing the BIOS version of GRUB Legacy to /dev/sda1 instead of /dev/sda3 will probably do absolutely no good, since /dev/sda1 is an EFI System Partition, which is a FAT partition that normally has no BIOS boot loader code in it. Installing GRUB Legacy to /dev/sda (that is, to the MBR, to overwrite the unused GRUB 2) might be more beneficial, as I suggested in my earlier post.

There's a slim possibility that wiping the useless GRUB code from the MBR will enable rEFIt to properly detect and launch the GRUB Legacy on the Linux partition. To do this, type the following command from a rescue disc:

```

sudo dd if=/dev/zero of=/dev/sda bs=440 count=1

```

Be very careful with this command, though, and particularly with the "bs=440" and "count=1" options; if you write too much data, you'll damage your partitions.

---

### Post by madtowneast on 2011-07-25
> **srs5694 said:**
> I'm not sure exactly what program or options you're seeing in the Fedora installer. I recommend you boot with [System Rescue CD](http://www.sysresccd.org) or [Parted Magic](http://partedmagic.com) and use GParted, parted, or gdisk, as described in my earlier post.

Please clarify what you mean by this. What tool did you use and precisely what did you do with it? Some possible interpretations of what you might mean by this are *extremely* dangerous, so I'd really like to understand what you've actually done before advising you further. It might be good for you to post another Boot Info Script output, or the output of "sudo parted /dev/sda print" or "sudo gdisk -l /dev/sda" so we can see the current state of your partition table, if you've been making changes to it.

I used the Ubuntu LiveCD version of GParted to unset the boot flag on the Fedora install (sda3) and then used Disk Utility (same program on both Ubuntu and Fedora) to change the partition type from EFI System Partition to MBR Partition Scheme, since some googling revealed that MBR Partition scheme is supposed to be the same as ghe gdisk code 0700. Fedora has this Disk Utility installed but nothing like GParted. Neither LiveCD has gdisk.

> **srs5694 said:**
> When reporting errors from programs it's imperative that you give a *verbatim* copy of the error message. If text-mode, copy-and-paste the error to this forum. If it's more than a few words, and especially if it contains formatted text, post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility. If it's a GUI program, post a screen shot. I've never heard of a "no bios driver installed" GRUB message, and I'm not entirely sure what that would mean, so I suspect you may have subtly altered the message in relaying it.

The error is:

```
[root@localhost liveuser]# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
/dev/mapper/../dm-0 does not have any corresponding BIOS drive.
```

> **srs5694 said:**
> I've never used Rescatux, so I can't comment on it.

Installing the BIOS version of GRUB Legacy to /dev/sda1 instead of /dev/sda3 will probably do absolutely no good, since /dev/sda1 is an EFI System Partition, which is a FAT partition that normally has no BIOS boot loader code in it. Installing GRUB Legacy to /dev/sda (that is, to the MBR, to overwrite the unused GRUB 2) might be more beneficial, as I suggested in my earlier post.

There's a slim possibility that wiping the useless GRUB code from the MBR will enable rEFIt to properly detect and launch the GRUB Legacy on the Linux partition. To do this, type the following command from a rescue disc:

```

sudo dd if=/dev/zero of=/dev/sda bs=440 count=1

```

Be very careful with this command, though, and particularly with the "bs=440" and "count=1" options; if you write too much data, you'll damage your partitions.v

I think i will try using SuperGrubDisk first before DDing.

---

### Post by srs5694 on 2011-07-25
> **madtowneast said:**
> I used the Ubuntu LiveCD version of GParted to unset the boot flag on the Fedora install (sda3) and then used Disk Utility (same program on both Ubuntu and Fedora) to change the partition type from EFI System Partition to MBR Partition Scheme, since some googling revealed that MBR Partition scheme is supposed to be the same as ghe gdisk code 0700. Fedora has this Disk Utility installed but nothing like GParted. Neither LiveCD has gdisk.

No, "MBR partition scheme" is a type code reserved for partitions that will themselves contain an MBR -- say, for use by a virtual machine. You should definitely *not* give a Linux partition that type code. A GPT Linux partition should have no flags (as viewed under GParted) or should have a type code of 0700 or 8300 (as viewed under gdisk). Furthermore, AFAIK, you can't set that type code in parted or GParted, so I really have no idea what you've done with your disk. Once again, please post the output of "sudo gdisk -l /dev/sda" or "sudo parted /dev/sda print".

You can install gdisk in an Ubuntu live CD by typing "sudo apt-get install gdisk" or by downloading the package for your version and double-clicking it in the desktop. (See download links [here.](http://www.rodsbooks.com/gdisk/download.html#obs)) Alternatively, you can use an emergency disc like [PartedMagic](http://partedmagic.com), which comes with parted and gdisk pre-installed.

> The error is:

```
[root@localhost liveuser]# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
/dev/mapper/../dm-0 does not have any corresponding BIOS drive.
```

As I suspected, that's quite different from what you initially reported ("it just gave me error saying that there is no bios driver installed"). A "BIOS drive" refers to the BIOS identification code for a hard disk, whereas a "BIOS driver" would perhaps be some sort of software to interface to a BIOS subsystem, although there's not much that qualifies as that under Linux, or perhaps a driver loaded by the BIOS.

The actual message indicates that the specified device file can't be tied to a specific BIOS-accessible hard disk. This is actually normal for a device in /dev/mapper, so it's not really an error, and I don't think this is an error message.

Did grub-install report anything else, or was that the complete output? Normally it finishes with something like:

```
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

# this device map was generated by anaconda
(fd0)     /dev/fd0
(hd0)     /dev/sda

```

If you saw output like that, then GRUB installed correctly. If you saw some other output, then perhaps something *else* went wrong and you've ignored the true error message because of confusion about the meaning of the message you did report.

---

### Post by madtowneast on 2011-07-25
> **srs5694 said:**
> No, "MBR partition scheme" is a type code reserved for partitions that will themselves contain an MBR -- say, for use by a virtual machine. You should definitely *not* give a Linux partition that type code. A GPT Linux partition should have no flags (as viewed under GParted) or should have a type code of 0700 or 8300 (as viewed under gdisk). Furthermore, AFAIK, you can't set that type code in parted or GParted, so I really have no idea what you've done with your disk. Once again, please post the output of "sudo gdisk -l /dev/sda" or "sudo parted /dev/sda print".

You can install gdisk in an Ubuntu live CD by typing "sudo apt-get install gdisk" or by downloading the package for your version and double-clicking it in the desktop. (See download links [here.]("http://www.rodsbooks.com/gdisk/download.html#obs")) Alternatively, you can use an emergency disc like [PartedMagic]("http://partedmagic.com"), which comes with parted and gdisk pre-installed.

gdisk gives the following output:

```

GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4F70BCB4-872D-4B1F-9983-F1B0AEC2E4DD
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 1517 sectors (758.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition333
   2          409640       658612775   313.9 GiB   AF00  Untitled 13333333333333
   3       658614272       968384511   147.7 GiB   EF01  33333333333333333333333
   4       968384512       976773119   4.0 GiB     8200  33333333333333333333333

```

There is no flag set on the drive anymore according to GParted
> **srs5694 said:**
> As I suspected, that's quite different from what you initially reported ("it just gave me error saying that there is no bios driver installed"). A "BIOS drive" refers to the BIOS identification code for a hard disk, whereas a "BIOS driver" would perhaps be some sort of software to interface to a BIOS subsystem, although there's not much that qualifies as that under Linux, or perhaps a driver loaded by the BIOS.

The actual message indicates that the specified device file can't be tied to a specific BIOS-accessible hard disk. This is actually normal for a device in /dev/mapper, so it's not really an error, and I don't think this is an error message.

Did grub-install report anything else, or was that the complete output? Normally it finishes with something like:

```
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

# this device map was generated by anaconda
(fd0)     /dev/fd0
(hd0)     /dev/sda

```If you saw output like that, then GRUB installed correctly. If you saw some other output, then perhaps something *else* went wrong and you've ignored the true error message because of confusion about the meaning of the message you did report.
 
No the error message is all i got and then I just add another terminal line

---

### Post by srs5694 on 2011-07-26
Well, then, first things first: Using gdisk, change the type code of /dev/sda3 to 0700. Type code EF01 (MBR partition scheme) is wrong. At best it will cause no problems, but at worst it'll cause GRUB to fail. Once that's changed, see if you can boot, and if you can't, try re-installing GRUB to /dev/sda.

---

### Post by madtowneast on 2011-07-26
So something like:

```

#gdisk /dev/sda3

GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Command (? for help): t


```

---

### Post by srs5694 on 2011-07-26
That's incomplete, but it's a start. After typing "t", you type the type code ("0700"), then at the next Command prompt you'd type "w" to save the changes.

---

### Post by madtowneast on 2011-07-26
Tried it all and still wont work. I cant boot off SuperGrubDisk, just sits there at 

```
Loading stage 2......
```

Here is the output of gdisk and the result of trying to install grub:

```
[root@localhost liveuser]# grub-install /dev/sda
/dev/mapper/../dm-0 does not have any corresponding BIOS drive.
[root@localhost liveuser]# gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.7.2

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4F70BCB4-872D-4B1F-9983-F1B0AEC2E4DD
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 1517 sectors (758.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       658612775   313.9 GiB   AF00  Untitled 1
   3       658614272       968384511   147.7 GiB   0700  
   4       968384512       976773119   4.0 GiB     8200  
[root@localhost liveuser]# 

```

The boot info script results are attached.

After doing the whole change I had to realign the MBR using the rEFIt partition tool because else I just got a prompt saying that it is looking for a bootable device.

---

### Post by srs5694 on 2011-07-26
What's the contents of the /dev/mapper directory? Perhaps you've got some leftover RAID data that's interfering with GRUB's ability to install to the disk.

My other suggestion at this point is to install an EFI-capable boot loader for Linux. My own preference, [ELILO,](http://elilo.sourceforge.net/) seems not to be too reliable on Macs; but you could try an EFI-enabled version of GRUB. Fedora ships with a hacked version of GRUB Legacy with EFI support, but I know relatively little about it. (It may already be installed and not working well; that could be that's why you're seeing two Linux options in rEFIt with identical results.) The only other option is GRUB 2. I don't know offhand if there's a prebuilt GRUB 2 for EFI for Fedora, but [this page](https://help.ubuntu.com/community/UEFIBooting) describes how to get it working from source code.

---

### Post by madtowneast on 2011-07-26
After some arm twisting of the installer I got the installer to install grub on sda, so grub2 is now gone. Thank you very much for your help.

---

