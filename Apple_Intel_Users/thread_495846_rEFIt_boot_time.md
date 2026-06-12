---
title: "rEFIt boot time"
date: 2007-07-08
forum: Apple Intel Users
---

### Post by sprucio on 2007-07-08
I have a triple boot setup with OS X, Linux and Windows (NTFS). When I boot my computer, it takes about 20 seconds before I see the icons from rEFIt. Is this normal?

---

### Post by russo.mic on 2007-07-08
Do you have a USB thumb drive or a CD or DVD in the optical drive?  Refit takes longer if there are other volumes on the computer, as it's trying to probe them to find out if there bootable.  

Russo

---

### Post by sprucio on 2007-07-08
None. Basically, if I can get verification about this from someone who has Windows with a NTFS setup, that would be helpful.

---

### Post by Chrisj303 on 2007-07-10
^ I'm triple booting OSX/UBUNTU/VISTA (using NTFS), and it only takes 2 seconds for all the rEFIt icons to show up on boot.

Like a previous poster touched on, it takes longer if i have other media connected - esp.DVD's.

---

### Post by grim1234 on 2007-07-10
do you have more than 4 partitions (including the hidden hfs partition for osx)?

do you have any external drives plugged in?

Perhaps it's a bug in refit, maybe you could submit it somewhere.

---

### Post by cyberdork33 on 2007-07-10
> **grim1234 said:**
> (including the hidden hfs partition for osx)?

Huh? 

By default you should have 2 partitions at a minimum. A FAT32 EFI partition and an HFS+ OSX partition.

Adding in Ubuntu and Windows makes 4, unless you made a swap. If this is the case, having 5 primary partitions could be the issue as it attempts to figure out how to handle this situation (as a legacy BIOS can only see 4 primary partitions).

---

### Post by sprucio on 2007-07-10
When I run diskutil, I see 0-4.

0: GUID Partition Scheme
1: EFI   200MB
2. Mac OS X  32.0GB (Mac Partition)
3. EFI 39.5GB (Linux EXT3)
4. Microsoft Basic Data Untitled 40.0GB (MS NTFS)

Chrisj303: would you mind posting your output for diskutil? I'd really like to see what I'm doing wrong here.

---

### Post by russo.mic on 2007-07-29
I don't think your supposed to have the 39 GB EFI partiton, that should be your linux partiton I think.  I wonder if having the volume label EFI is a problem?  did you install EFI in MacOSX and linux?  Maybe just to use the sync tool?  maybe something there got funny...Hmmmm..dunno.


Russo

---

### Post by ronocdh on 2007-07-29
> **russo.mic said:**
> I don't think your supposed to have the 39 GB EFI partiton, that should be your linux partiton I think.  I wonder if having the volume label EFI is a problem?  did you install EFI in MacOSX and linux?  Maybe just to use the sync tool?  maybe something there got funny...Hmmmm..dunno.


Russo
This made me smile. I really hope it was a typo on sprucio's part that the volume was listed with the label "EFI," but I suppose we shall find out. Interesting if that's the problem! Perhaps most because I can't imagine what would possess someone to choose that volume label.... ;)

---

