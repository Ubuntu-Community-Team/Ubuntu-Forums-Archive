---
title: "Mounting a drive...with a twist"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by squagles on 2005-10-16
Hello.

I'm new to the forums and have a question about mounting drives.  I've looked through some of the other threads on this topic and still haven't found the info or instructions I am looking for.

Anyway I have just recently installed Ubuntu 5.10.  Everything worked fine and my hard drive and cdrom both work and I'm not having any trouble with those.  However I did back up a bunch of music files on a hard drive that I'm going to be giving to a friend.  I was wondering what would be the easiest way to mount that drive so that I can transfer these files to my main hard drive.  I'm not looking for a permenant setup, just a one time transfer.  I'm not sure whether the FS is FAT or NTFS, I just formatted it using the command line "format" tool in Windows XP, so whatever FS that sets up by default would be what it is.

The only method I tried is unplugging my cdrom and plugging in the hard drive, in the same slot.  Any advice on how to move these files would be greatly appreciated.  I have a *some* experience with linux, mainly command line stuff from working on servers.  I've never mounted anything though.

Thanks in advance.

---

### Post by aysiu on 2005-10-16
Can I assume this is an actual hard drive you've temporarily installed (as opposed to a USB drive)? If so, typing ```
sudo fdisk -l
``` in the terminal will tell you where it's attached (probably something like */dev/sdb1*) and what type it is (*fat32* or *NTFS*). Once you know where it's located and what type it is, follow these directions to mount it:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by squagles on 2005-10-16
My friend who I called about this just kept saying "run fdisk, you'll see it".  He left off the ever so important **-l**.  Thanks for the help.

---

