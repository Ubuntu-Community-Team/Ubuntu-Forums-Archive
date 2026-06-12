---
title: "iMac5,1 hardy wont launch from rEFIt"
date: 2008-07-27
forum: Apple Hardware Users
---

### Post by tsr on 2008-07-27
Hi,

When I first got my iMac (5.1 17" screen) I tried to follow the instructions to install ubu6.04 and failed.

Now, since my real comp a generic laptop has died I'm trying again.

I've downloaded the install (32 bits) disk of ubu 8.04, burnt it and booted with it. (I don't get to make a choice in the boot-menu since it gets covered in a non-removable language-selection menu).

Either way the liveCD gets going and I'm able to install ubuntu (using manual partition to keep my efi partion and MacOS X partitions).

Every thing gets installed and I'm asked to reboot...

In the rEFIt-menu (I've updated rEFIt to version 0.11) I have three choices:
- a penguin to boot with lilo.conf
- mac
- a penguin to boot from HD

The first option gives: "invalid configuration in lilo.conf" (or something similar)

The second boots MacOS X (I'm on Tiger 10.4.11)

The third just smacks a small penguin in the middle of the screen and then stops working (I've tried waiting for 10 mins but still nothing).

I'd prefer to not have to wipe the HD as I don't have a back-up device for the media files that I've got into there (since my laptop died).

Any hints? Do you need more info?

Thanks, tsr

---

### Post by cyberdork33 on 2008-07-27
There is an installation bug in Hardy, thoughyour errors sound a bit different.

---

### Post by tsr on 2008-07-28
Ok, maybe it is that bug, can you tell me more about it?

I'm willing to try anything :)

Is there any way to do it all from the beginning without losing my MacOS X install?

/tsr

---

### Post by hajk on 2008-07-28
Have you by any chance forgotten to synch the GUID and MBR partition tables? Just in case: in the rEFIt boot menu use the arrow keys to select the Partitioner Tool and confirm with "yes". Then, again with the arrow keys in rEFIt, select the restart button.

---

### Post by cyberdork33 on 2008-07-28
Sorry, I got pulled away when posting the last reply.

Please have a look in the FAQ. There is a link to the Install Bug fix there. The lilo error is a strange one and might need to more details to be able to see what is going on since you shouldn't even have lilo installed at this point since it does not come with a default install of Ubuntu.  I think it might be a leftover from your previous attempts to get things working.
[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

Please give the output of the following commands in the Ubuntu LiveCD environment:
List the MBR Partition Table
```
sudo fdisk -l /dev/sda
```
List the GPT:
```
sudo parted /dev/sda print
```

You cannot select a language when booting from the LiveCD because of a firmware issue on your Mac related to your keyboard. Since you have an iMac5,1 this should be fixed if you apply all the updates in OSX.

---

### Post by tsr on 2008-07-28
> **hajk said:**
> Have you by any chance forgotten to synch the GUID and MBR partition tables? Just in case: in the rEFIt boot menu use the arrow keys to select the Partitioner Tool and confirm with "yes". Then, again with the arrow keys in rEFIt, select the restart button.

Well according to the partition tool nothing needs syncing...

/tsr

---

### Post by tsr on 2008-07-28
Ok, thanks for giving me a hand, here are the results:

```

sudo fdisk -l /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2   *          26        6537    52297728   af  Unknown
/dev/sda3           19199       19457     2075980+  82  Linux swap / Solaris
/dev/sda4            6537       19199   101709824   83  Linux

Partition table entries are not in disk order

```

and

```

sudo parted /dev/sda print


Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot 
 2      210MB   53.8GB  53.6GB  hfs+         Apple_HFS_Untitled_1       
 4      53.8GB  158GB   104GB   ext3                                    
 3      158GB   160GB   2126MB  linux-swap                              

Information: Don't forget to update /etc/fstab, if necessary.   

```

Oh, and I tried to boot from holding down the alt-key during start-up and that worked.

Ofc, now I have to get the ndiswrapper and co going to be able to access the intarweb :)

/tsr - two different steps at a time

---

### Post by cyberdork33 on 2008-07-28
Well all your partitions look good. I would venture to guess that you likely have lilo installed in the MBR from your previous attempt, and you current install didn't go over well because of the install bug. You should try reinstalling GRUB to the MBR to overwrite what might be there now.

At least we know that the system is bootable now.

---

### Post by tsr on 2008-07-28
> **cyberdork33 said:**
> Well all your partitions look good. I would venture to guess that you likely have lilo installed in the MBR from your previous attempt, and you current install didn't go over well because of the install bug. You should try reinstalling GRUB to the MBR to overwrite what might be there now.

At least we know that the system is bootable now.

Great, how do I do that.

/tsr - feeling n00by

---

### Post by cyberdork33 on 2008-07-28
> **tsr said:**
> Great, how do I do that.

/tsr - feeling n00by
Sorry, never linked to it. The link fpr the install bug is in the FAQ...

[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

---

### Post by tsr on 2008-07-28
Ok, now it works, sort of.

I've got 4 main choices now:
1. Tux - tries to load something from lilo but fails by not finding anythin
2. Apple - loads my Tiger
3. Tux - loads Ubuntu from HD (but it takes 10 secs to get from rEFIt to grub, is that normal)
4. Tux - I havent tried this but it says it wants to load from partition 4 (which by number is a swap partition but in order is the main Ubuntu partition)

So if this menu can be fixed in anyway, I'd appreciate the help.

I've found [this]("http://sourceforge.net/tracker/index.php?func=detail&aid=1674574&group_id=161917&atid=821764") and [this]("http://sourceforge.net/tracker/index.php?func=detail&aid=1535014&group_id=161917&atid=821764") on the EFI-tracker but I don't dare to try stuff if I risk to mess things up.

/tsr

---

### Post by cyberdork33 on 2008-07-28
> **tsr said:**
> Ok, now it works, sort of.

I've got 4 main choices now:
1. Tux - tries to load something from lilo but fails by not finding anythin
2. Apple - loads my Tiger
3. Tux - loads Ubuntu from HD (but it takes 10 secs to get from rEFIt to grub, is that normal)
4. Tux - I havent tried this but it says it wants to load from partition 4 (which by number is a swap partition but in order is the main Ubuntu partition)

So if this menu can be fixed in anyway, I'd appreciate the help.

I've found [this]("http://sourceforge.net/tracker/index.php?func=detail&aid=1674574&group_id=161917&atid=821764") and [this]("http://sourceforge.net/tracker/index.php?func=detail&aid=1535014&group_id=161917&atid=821764") on the EFI-tracker but I don't dare to try stuff if I risk to mess things up.

/tsr
Unfortunately, that seems like the only solution... (at least for one of the icons.) I wrote a thread on clearing the bootloader in the MBR here:
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

partition 4 (sda4) is your Linux root partition. that one should bring up grub as well. Try clearing the MBR bootcode and see what is left.

---

### Post by tsr on 2008-07-28
> **cyberdork33 said:**
> Unfortunately, that seems like the only solution... (at least for one of the icons.) I wrote a thread on clearing the bootloader in the MBR here:
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

partition 4 (sda4) is your Linux root partition. that one should bring up grub as well. Try clearing the MBR bootcode and see what is left.

Ookeeey...

I tried the steps (including reverting :)) but the only thing I've accomplished so far is that I can't boot up Tiger. Grub is loaded and starts Ubuntu (after a lot of waiting, but still).

I mean I don't get to any form of boot-up menu. I haven't really tried using the 'alt' trick but anyway.

Is there any way to get things back or should I considering it working now?

(I mean I can mount my Mac partition and get all my essential files from it (not that there are many, just some movies/songs))

/tsr

---

### Post by cyberdork33 on 2008-07-28
well honestly I don't know how that would have messed up your OSX install.

You can try booting an OSX DVD and blessing the OSX partition, but if it still won't boot I don't know where to go. Really sorry about that. You do seem to have something strangely configured somehow, but I can't figure out what it might be.

---

### Post by tsr on 2008-07-29
> **cyberdork33 said:**
> well honestly I don't know how that would have messed up your OSX install.

You can try booting an OSX DVD and blessing the OSX partition, but if it still won't boot I don't know where to go. Really sorry about that. You do seem to have something strangely configured somehow, but I can't figure out what it might be.
Not your fault, I did it at my own risk, dont worry about it.

I managed to make the efi-partition bootanle again so now at least I got that menu back. I'll look into the blessing thing later.

Thanks for all your help, couldn't have done it without you.

/tsr

---

