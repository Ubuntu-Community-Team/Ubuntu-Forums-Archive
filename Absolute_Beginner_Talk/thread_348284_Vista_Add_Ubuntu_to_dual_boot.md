---
title: "Vista: Add Ubuntu to dual boot"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by macrho on 2007-01-28
I'm about as green as you can get in trying Ubuntu.

Here's my current setup:

I have a laptop running Vista (RTM). I have 2 partitions, one 68GB and running Vista, the other (NTFS formatted but nothing on it) 23.3GBs. Both are primary partitions.

I would like to install Ubuntu on my 23.3GB partition and dual boot between Vista and Unbuntu.

I downloaded the ISO and booted off my CD and I was intrigued enough to want to try and install.  From within the Unbuntu install program, I could not determine how to tell it to install simply to my 23.3 GB partition instead of the whole drive -- how does one do this?

and once the install is completed, is EasyBCD the best boot manager? I noticed their wikis were down or required registration.

Anyway, I'm a clueless user hoping for help....

---

### Post by Shatrat on 2007-01-28
You could use the manual partitioning to delete the 23gb partition, create a 2g (or at least, something just a bit larger than your ammount of RAM) swap partition, and the rest for an ext3 partition.
Ubuntu will automatically install Grub and should have an entry in it to boot the windows partition as well as Ubuntu.
If you want more info here is a nice place to start.
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
You'll notice there is a Dual Boot page linked from there.

---

### Post by macrho on 2007-01-28
I was able to delete the partition and create a swap and ext3 one, however, when I attempt to move forward, my remaining 68GB partition wants to be mounted as /media3 or something like that. I guess I'm erring on the side of caution and not proceeding as I'm unsure as to what it will do if I hit next.

Again thanks for any help.

---

### Post by audax321 on 2007-01-28
There is a difference between mounting and formatting. Formatting means the drive partition will be erased and/or a new type of filesystem will be put in its place.

Filesystems get mounted in both Windows and Linux. They get mounted in Windows too, but the mount is usually to a drive letter. "To mount" just means to make the filesystem readable by the person using the operating system at a particular point (e.g. a drive letter). Linux doesn't use drive letters. In Linux a filesystem can be mounted to ANY folder under the root filesystem (designated by /) depending on the permissions you have.

So, if its mounting the Vista partition to /media then its mounting it so when you are in Linux you can access the media folder under the / filesystem to access files in the Vista partition. It shouldn't be formatting it unless it specifically says so (e.g. has an alternate filesystem listed)... I don't know how the installer will act toward a Vista partition since MS may have made changes to the filesystem (if its the same old NTFS of previous Windows versions, then it should be fine to mount). Although I would recommend changing the /media3 mount location to something that makes more sense, like /media/Vista or something. In any case BACK UP before doing anything like this, especially if its the first time you're trying out Linux, you don't want any small mistakes turning into a major problem resulting in data loss.

Hope that helps and here is a link explaining it in other terms if I wasn't clear:
[http://whatis.techtarget.com/definition/0,,sid9_gci214638,00.html](http://whatis.techtarget.com/definition/0,,sid9_gci214638,00.html)

---

