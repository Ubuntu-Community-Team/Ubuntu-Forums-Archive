---
title: "Mounting HFS+ drive"
date: 2011-12-16
forum: Apple Hardware Users
---

### Post by ubunwhat on 2011-12-16
Sorry for the repost.  I posted this question a few minutes ago but somehow labelled it as lubuntu, and I couldn't edit that back to ubuntu.  Anyway, it is a Ubuntu problem, and the issue is as follows:

I am trying to recover some data from a drive that was in a mac book.  It is an HFS+ drive that I am trying to mount the drive via USB, so I don't need to boot to it or anything.  I just need read access.  I don't even need to write to the drive.  However, every time I try to mount the drive I get the following error:

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I'm lost as to how to proceed.  I've seen articles that say it is possible to get not just read, but read / write access on HFS+ drives, but I'm not a terminal wizard by any stretch and couldn't get much of anything to work.  I think that they were all referring to how to mount the drive as a boot drive, which is not what I need to accomplish.  Anyway, I'm open to suggestions here.

---

### Post by ajgreeny on 2011-12-17
What command are you using to mount the partition?

You must first make sure that you have the mount folder to mount to, then use a command like ```
sudo mount -t hfsplus /dev/sdx# /mnt/folder
```having first made that folder as mountpoint.

See [http://ubuntuforums.org/showthread.php?t=1076577](http://ubuntuforums.org/showthread.php?t=1076577) and [http://ubuntuforums.org/archive/index.php/t-1485096.html](http://ubuntuforums.org/archive/index.php/t-1485096.html) for further details.

---

### Post by ubunwhat on 2011-12-17
I read those threads and they confused me.  First of all, I'm not trying to boot to the drive, which seems to be the point of those threads.  I don't need to write to it either.  I need to access it via USB.  I just need to mount the thing long enough to read some data off of it.  Also, I have no idea how on earth I would create a mount folder on the drive if I can't read or write to it.

---

### Post by ubunwhat on 2011-12-17
I am trying to recover some data from a drive that was in a mac book. It is an HFS+ drive.  I am trying to mount the drive via USB, so I don't need to boot to it or anything. I just need read access. I don't even need to write to the drive. However, every time I try to mount the drive I get the following error:

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

I'm lost as to how to proceed. I've seen articles that say it is possible to get not just read, but read / write access on HFS+ drives, but I'm not a terminal wizard by any stretch and couldn't get much of anything to work. I think that they were all referring to how to mount the drive as a boot drive, which is not what I need to accomplish. I've been trying to use Disk Utility but not getting much love.  There is what appears to be a small partition on the drive that I am guessing is the boot partition.  I'm wondering if it would help if I either reformatted that small partition or deleted it entirely.  But that's just desperation talking.  Anyway, I'm open to suggestions here.

---

### Post by coffeecat on 2011-12-17
HFS+ partitions will mount read-only in Ubuntu. If the HFS+ filesystem is non-journalled, then it will mount read-write. The error you are getting sounds as though there is filesystem corruption and I don't believe you will be able to repair this in Ubuntu.

The small partition is the EFI partition. You won't achieve anything by deleting it, I'm afraid.

How are you trying to mount the partition? It *should* automount as soon as you plug it in, unless of course there is filesystem damage. Do you have access to an Apple machine? It would be advisable to see if you can repair the partition with MacOS, after which you should be able to read it in Ubuntu.

---

### Post by ubunwhat on 2011-12-17
The Mac Book is down, which is why I am trying to recover the data.  As for how I am mounting, again, I'm not a wizard at any of this by a long shot.  Essentially I plug it into my usb and it shows up as a drive in my file system.  When I try to access it by clicking on it I am told that I have to mount the drive first.  I go into Disk Utility where the drive does show up and I can see the partitions.  When I click Mount Volume I get the message I posted above.  I've read several threads about mounting via terminal but they go right over my head.  I'm told I have to create a folder on the drive to mount to, but I can't fathom how I can create a folder on it if I can't mount it.  I'm probably just not understand most / all of this, but I'm trying to hack my way through it.

---

### Post by coffeecat on 2011-12-17
> **ubunwhat said:**
> The Mac Book is down, which is why I am trying to recover the data.  As for how I am mounting, again, I'm not a wizard at any of this by a long shot.  Essentially I plug it into my usb and it shows up as a drive in my file system.  When I try to access it by clicking on it I am told that I have to mount the drive first.  I go into Disk Utility where the drive does show up and I can see the partitions.  When I click Mount Volume I get the message I posted above.  I've read several threads about mounting via terminal but they go right over my head.  I'm told I have to create a folder on the drive to mount to, but I can't fathom how I can create a folder on it if I can't mount it.  I'm probably just not understand most / all of this, but I'm trying to hack my way through it.

OK, I follow you.

What should happen is that you plug it in, it appears in the left pane of a Nautilus window (if you have one open), and another Nautilus window should open showing the contents of the partition, which you can then browse. You don't need to open Disk Utility at all, or use the terminal. So - when you say "it shows up as a drive in my file system", what exactly happens? Does it show an entry in the left "Places" pane of Nautilus?

Whether it does or not, the error message you are getting suggests a filesystem problem. If so, you can only repair this with MacOS. When I asked you if you had access to an Apple machine, I meant another Apple machine - perhaps a friend's. I realise that the MacBook is inoperable.

---

### Post by ubunwhat on 2011-12-17
It does indeed show up in the left side of a Nautilus pane.  That is where I click from and get the message that I must first mount the drive.  Disk Utility was just a stab in the dark, I guess.

---

### Post by coffeecat on 2011-12-17
> **ubunwhat said:**
> It does indeed show up in the left side of a Nautilus pane.  That is where I click from and get the message that I must first mount the drive.  Disk Utility was just a stab in the dark, I guess.

Yes, this all adds up to a dirty filesystem, I guess. I do have to correct myself on one point though. If you install the package hfsprogs, you do get a command line fsck.hfsplus, which in theory you could use to fix the filesystem. However, if your HFS+ filesystem is journalled, which it almost certainly is, then you have to use the force option in order to carry out a filesystem check. I've just been experimenting on a freshly formatted HFS+ drive. I would not recommend using the force option on a filesystem that could already be damaged, which means that you do really need to use MacOS to check this drive out.

As an aside, and to amend something I said in my first post here, you can mount a (clean) journalled HFS+ fileystem read-write in Ubuntu, but you have to do this from the terminal and again you have to use the force option. Not something I would do myself and not something I would recommend.

Sorry - unless someone else has any other ideas, I really think you need to see if you can use another Mac.

If you do manage to repair the filesystem in MacOS there will be one more hurdle to cross. Your UID (user identity) in your Mac files will likely be 99, and in Ubuntu your account UID will probably be 1000. Which means that you won't be able to open some of the folders in your HFS+ home folder. You will need root privileges with a "gksu nautilus" file browser.

---

### Post by Lars Noodén on 2011-12-17
Have you installed the HFS+ support?  There are packages hfsplus, hfsutils, and hfsprogs.  You need to have at least one of them (I can't remember which one) to mount HFS. I have all three installed and mount HFS+ regularly.

---

### Post by ubunwhat on 2011-12-17
> **coffeecat said:**
> Yes, this all adds up to a dirty filesystem, I guess. I do have to correct myself on one point though. If you install the package hfsprogs, you do get a command line fsck.hfsplus, which in theory you could use to fix the filesystem. However, if your HFS+ filesystem is journalled, which it almost certainly is, then you have to use the force option in order to carry out a filesystem check. I've just been experimenting on a freshly formatted HFS+ drive. I would not recommend using the force option on a filesystem that could already be damaged, which means that you do really need to use MacOS to check this drive out.

As an aside, and to amend something I said in my first post here, you can mount a (clean) journalled HFS+ fileystem read-write in Ubuntu, but you have to do this from the terminal and again you have to use the force option. Not something I would do myself and not something I would recommend.

Sorry - unless someone else has any other ideas, I really think you need to see if you can use another Mac.

If you do manage to repair the filesystem in MacOS there will be one more hurdle to cross. Your UID (user identity) in your Mac files will likely be 99, and in Ubuntu your account UID will probably be 1000. Which means that you won't be able to open some of the folders in your HFS+ home folder. You will need root privileges with a "gksu nautilus" file browser.

Can you tell me more about the fsk.hfsplus?  How would I use it from the command line, etc?

---

### Post by howefield on 2011-12-17
Duplicate threads merged.

---

### Post by ubunwhat on 2011-12-17
Just when I think I'm getting the hang of this....

I have installed all of the hfs+ tools.  I connect the hfs+ drive via usb and try to run fsck.hfsplus on the drive but I get an error that says I don't have permission to access the drive.  I've tried it using force mode but still get the same response.  I was prepared to run into permission errors when I was trying to access specific folders, but I did not know it was even possible to run into a permission errors just trying to prepare the drive for mount.  Any ideas?

---

### Post by fdrake on 2011-12-17
plug your usb, type and post the output of:

```

sudo fdisk -l

```

---

### Post by ubunwhat on 2011-12-17
WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000680a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7296    58605116   ee  GPT

---

### Post by ajgreeny on 2011-12-17
For a mac formatted disk and partitions you need to use the terminal command ```
sudo parted -l
``` not ```
sudo fdisk -l
``` hence the warning you got from fdisk.

---

### Post by ubunwhat on 2011-12-17
I wasn't trying to use fdisk at all.  I was trying to use fsck.hfsplus, which is part of hfsprogs.

---

### Post by fdrake on 2011-12-18
"parted" doesn't come by default so you have to install it."sudo apt-get install parted". Also fdisk gives enough informations about the name of the partition/hdd-drive, so we can you fsck.hfsplus.
```

sudo umount /dev/sdc1
sudo fsck.hfsplus -y -d -c 1024 /dev/sdc1

```

---

### Post by skullmunky on 2011-12-19
Using any of the disk utility / management tools from the command line will always require "sudo" at the beginning to run with admin privileges.  

In your first post you said the error you got was 

```

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
missing codepage or helper program, or other error

```

So the partition you're trying to repair is probably /dev/sdb2.  :D  

That's the second partition on the drive, with all your stuff on it.  On a Mac boot drive the first partition (here, /dev/sdb1), is the EFI boot partition.  

To run fsck on it you should then just be able to do this:

```

sudo fsck /dev/sdb2

```

fsck can often figure out what the file system type is automatically.  If it can't ("wrong fs type", etc... ) then that's when you'd use the explicit fsck.hfsplus.  

It's a good point about the journaling, you might not be able to fix it using linux tools because of that.  

For fixing mac disks I've had decent luck with Diskwarrior, but be prepared to spend a loooooooooooooooooooong time with it.  It's really a shame that mac disks are so fragile ...

---

### Post by fdrake on 2011-12-19
@ skullmunky : good catch,sir! I totally skipped the error msg with the device name....

---

