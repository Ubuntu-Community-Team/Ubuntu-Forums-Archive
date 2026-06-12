---
title: "MacBook triple boot Windows XP problem"
date: 2007-10-04
forum: Apple Intel Users
---

### Post by Room 34 on 2007-10-04
First off, apologies for newbie-isms. I did some searching before posting this, to no avail. If my question is answered in another thread, please post a link.

I am new to Ubuntu, just installed it in a triple-boot configuration on my MacBook over the weekend. I am running Mac OS X 10.4.10, Ubuntu 7.04, and Windows XP SP2. I'm using rEFIt 0.10 and GRUB. Reformatted the HD before this process. I'm not using Boot Camp at all (other than the Windows drivers CD), nor LILO (the need for that never even came up in the process, and I'm not even entirely sure what it does). I followed some instructions I found here and elsewhere to do the installation, and for the most part it was pretty seamless.

Now, on to my main issue: **Booting into Windows requires a weird "back-door" process.** I cannot select Windows from the rEFIt menu; doing so just makes the screen go black and the computer hangs. I can boot into Windows fine, but only if I select Ubuntu on the rEFIt menu, and then select Windows XP from the GRUB menu that follows. Again, booting up into all 3 OSes works, I am just wondering why I have to do this two-step process for Windows.

A related issue, I think: **Ubuntu can't mount the XP volume.** I get a message that there's an error in /etc/fstab. As I said I'm a Ubuntu n00b but I've done a fair amount of Linux (Fedora) command-line stuff at work, so I poked into fstab and couldn't find anything obviously wrong. I'm guessing there's something to do with the boot loaders and/or the partition map or other such low-level stuff I know little to nothing about.

Any suggestions here?

Again, to boil my ramblings down to two concise questions:

[B]1. Why do I have to select Ubuntu on rEFIt and then Windows XP on GRUB in order to boot Windows?
2. Why can Ubuntu see that the Windows volume exists, but it can't mount it?[/B]

Thanks in advance...

---

### Post by cyberdork33 on 2007-10-04
> **Room 34 said:**
> First off, apologies for newbie-isms. I did some searching before posting this, to no avail. If my question is answered in another thread, please post a link.

I am new to Ubuntu, just installed it in a triple-boot configuration on my MacBook over the weekend. I am running Mac OS X 10.4.10, Ubuntu 7.04, and Windows XP SP2. I'm using rEFIt 0.10 and GRUB. Reformatted the HD before this process. I'm not using Boot Camp at all (other than the Windows drivers CD), nor LILO (the need for that never even came up in the process, and I'm not even entirely sure what it does). I followed some instructions I found here and elsewhere to do the installation, and for the most part it was pretty seamless.

Now, on to my main issue: **Booting into Windows requires a weird "back-door" process.** I cannot select Windows from the rEFIt menu; doing so just makes the screen go black and the computer hangs. I can boot into Windows fine, but only if I select Ubuntu on the rEFIt menu, and then select Windows XP from the GRUB menu that follows. Again, booting up into all 3 OSes works, I am just wondering why I have to do this two-step process for Windows.

A related issue, I think: **Ubuntu can't mount the XP volume.** I get a message that there's an error in /etc/fstab. As I said I'm a Ubuntu n00b but I've done a fair amount of Linux (Fedora) command-line stuff at work, so I poked into fstab and couldn't find anything obviously wrong. I'm guessing there's something to do with the boot loaders and/or the partition map or other such low-level stuff I know little to nothing about.

Any suggestions here?

Again, to boil my ramblings down to two concise questions:

[B]1. Why do I have to select Ubuntu on rEFIt and then Windows XP on GRUB in order to boot Windows?
2. Why can Ubuntu see that the Windows volume exists, but it can't mount it?[/B]

Thanks in advance...

For the first problem, install grub to the ubuntu partition. If you don't want to reinstall Ubuntu (and click the advanced button at the end to select the partition to install grub to), then follow this:
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)
Note that grub starts counting at 0 for partitions, so sda1 = (hd0,0), sda2 = (hd0,1), etc.

Boot your Windows CD and start the recovery console. Use the FIXMBR command to reinstall the Windows bootloader to the MBR. This should allow you to select windows and linux from refit and boot directly to windows or ubuntu (grub).
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

For your mounting issue, please post your fstab, and any errors you get when trying to mount the partition.

---

### Post by Room 34 on 2007-10-04
Thanks... I was hoping the solution would be a bit more straightforward -- just editing a config file or running a CLI utility, not having to reinstall anything.  But I guess that's just how it goes.  I'll have to weigh whether or not I want to delve further into this at this point, since things ARE working, for the most part.

Actually, the inability to mount the Windows volume is probably more of a pressing issue, although since I CAN mount my Mac OS X volume, I can at least transfer files onto the Linux partition.  The only way to get them OUT though is to burn a CD.  I guess that begs a good question: if I'm able to mount the Windows partition, will I be able to write to it (it's FAT32) or will it be read-only like the Mac partition?

Here are the contents of my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2443e98f-525b-4fdd-8389-1d37201ee9d1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=EC5D-0AAF  /media/Untitled 3       vfat            defaults,utf8,umask=007,gid=46 0 1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Initially I assumed the problem was because I had renamed the Windows volume (from Mac OS X), and the fact that it was called "Untitled" here was the problem.  But changing that value didn't solve anything. So I think it's really those hex values that are the problem. I assume those are the start and end addresses of the volumes on the disk. (Again, this is much more low-level than I normally deal with, so I have to plead igorance.)

Thanks...

---

### Post by cyberdork33 on 2007-10-04
> **Room 34 said:**
> Thanks... I was hoping the solution would be a bit more straightforward -- just editing a config file or running a CLI utility, not having to reinstall anything.  But I guess that's just how it goes.  I'll have to weigh whether or not I want to delve further into this at this point, since things ARE working, for the most part.

Actually, the inability to mount the Windows volume is probably more of a pressing issue, although since I CAN mount my Mac OS X volume, I can at least transfer files onto the Linux partition.  The only way to get them OUT though is to burn a CD.  I guess that begs a good question: if I'm able to mount the Windows partition, will I be able to write to it (it's FAT32) or will it be read-only like the Mac partition?

Here are the contents of my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2443e98f-525b-4fdd-8389-1d37201ee9d1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=EC5D-0AAF  /media/Untitled 3       vfat            defaults,utf8,umask=007,gid=46 0 1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```Initially I assumed the problem was because I had renamed the Windows volume (from Mac OS X), and the fact that it was called "Untitled" here was the problem.  But changing that value didn't solve anything. So I think it's really those hex values that are the problem. I assume those are the start and end addresses of the volumes on the disk. (Again, this is much more low-level than I normally deal with, so I have to plead igorance.)

Thanks...
I am pretty sure the mounting issue is related to the space in your Folder name. 'Unititled 3'. try changing that to 'Untitled\ 3'. IDK if that will work either, and if not just change your folder name to something without a space...

FAT32 should mount read-write easily. NTFS can as well now with ntfs-3g. Your can mount your HFS+ (OSX) volume read-write if you turn off journalling on the filesystem. You will still have permissions issues though as linux recognizes the OSX permissions settings on files.

[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)
NOTE, sometimes you have to enable journaling before disabling it, even though it is already enabled... weird, i know...

---

### Post by Room 34 on 2007-10-04
> **cyberdork33 said:**
> I am pretty sure the mounting issue is related to the space in your Folder name. 'Unititled 3'. try changing that to 'Untitled\ 3'. IDK if that will work either, and if not just change your folder name to something without a space...

FAT32 should mount read-write easily. NTFS can as well now with ntfs-3g. Your can mount your HFS+ (OSX) volume read-write if you turn off journalling on the filesystem. You will still have permissions issues though as linux recognizes the OSX permissions settings on files.

[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)
NOTE, sometimes you have to enable journaling before disabling it, even though it is already enabled... weird, i know...

Sheesh! Thanks.. for some reason it never occurred to me that the "3" was part of the folder name!

---

### Post by Room 34 on 2007-10-11
Well... I didn't do anything consciously to fix this problem, but it's now fixed.  Clicking the Windows icon in the rEFIt menu at startup is working.  No more black screen.  Now, of course, clicking on either Linux or Windows brings me to the same place -- the GRUB menu.  But I can choose from there.  A bit inelegant, but it works just fine.

I haven't knowingly done anything that would affect the boot process, but I have run Update Manager a few times, and I've installed KDE and XFCE on top of my original Ubuntu 7.04 install.  Seems unlikely that any of that would have had an effect.  Now it's just a curiosity though.

---

### Post by Breepee on 2008-01-04
Sorry for the kick, but I have a question.

The topicstarter seems to have installed Windows on an (assumedly) GPT-drive, without bootcamp. I'd like to know how that's done, because now bootcamp isn't an option (for me) anymore I still would like to install Windows.

---

### Post by cyberdork33 on 2008-01-04
> **Breepee said:**
> Sorry for the kick, but I have a question.

The topicstarter seems to have installed Windows on an (assumedly) GPT-drive, without bootcamp. I'd like to know how that's done, because now bootcamp isn't an option (for me) anymore I still would like to install Windows.
Well, I haven't done it myself, but I would assume it is as easy as using a partitioning tool to shrink your OSX partition, then creating a partition for Windows and installing!

Boot camp is actually just a GUI for a commandline tool:
[http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes)

---

