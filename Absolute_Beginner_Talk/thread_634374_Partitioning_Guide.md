---
title: "Partitioning Guide"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by zesty on 2007-12-07
While setting up my new Ubuntu computer, I decided to customize my hard drive partitions.  Most guides recommend that inexperienced users simply use the default settings which automatically assign Root and Swap partitions.  This is the most space efficient method for smaller HDs and is certainly the easiest.  Many modern computers come with large hard drives which allows room for a more solid configuration.  Plus, half the fun of linux is creating a custom system.  Creating separate partitions will create a more solid system that can better serve your needs.

There's a lot of information out there on how to partition a HD.  There's many tools and tutorials at your disposal.  The best guide I've found is: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning).  The information I found to be missing was how much room to give those partitions.  What follows is information I collected and some of my opinions in an attempt to fill in some of that missing info.  I too, am a new user so do not take this guide as manual.  Its more my attempt to pass on what I've learned and I hope it can help someone get closer to their own perfect setup.  If you find corrections that should be made, please post them here.

The format is as follows:
**Type of Partition - Importance**
**mount:** what you enter for the partitioner
**type:** the partition formatting type
**location:** where on the drive the partition should be located.  This order is generally not important but its good to keep things organized
**size: ** The amount of disk space to allocate.  This will vary greatly depending on the system's intended use and the preferences of the user.  Partitions can be changed later without re-installing software.


Root - Required
mount: /
type: ext3
location: beginning
size:	NOTE: anywhere between 5-15GB
	A) If you have a small HD or will not use many programs = 5GB
	B) If you plan to use many programs and/or have a large HD = 15GB

SWAP - Required
mount: swap
type: not applicable
location: end
size:	NOTE:  This seems to be in debate. In general, the consensus seems to follow: Twice the size of RAM memory up to a partition size of 2GB.  1GB is generally considered a good amount.

Home - Recommended
mount: /home
type: ext3
location: middle
size:  NOTE: This partition will be where files and settings are stored.  This partition will allow the OS to be changed without affecting these files.  The size will depend on other optional setups.
	A) If no other partitions are needed this one should include all remaining space
	B) If most files or documents will be stored on another partition or drive, this partition could be as low as 5GB

Boot - Recommended*
mount: /boot
type: ext3
location: in front of Root if used
size: NOTE: I have not found much information on this.  I have heard that it needs to be 100-800MB.  
NOTE2:  Perhaps not needed, see posts below.

Linux/Windows Share - Optional
mount: (optional, could use /home/linuxshare)
type: fat32 (read/write by Linux and Windows)**
location: middle
size:  NOTE: This size will depend on how much data you wish to share.  Partitions for /home and /windows could be smaller if the bulk of files will be shared.
**NOTE2:  NTFS and ext3 may have some benefits above fat32.  All these filetypes can be read/write for Linux and Windows with new appropriate drivers.  See posts below.


MS Windows - Optional
mount: /windows
type: NTFS
location: middle
size:  NOTE:  Many recommendations have this partition as half the hard drive.  This size would depend on if you intend to have a share partition for files.  If this partition will just hold the OS, 10GB could be used.

---

### Post by nikoPSK on 2007-12-08
+1 

I vote this for sticky.

EDIT: I agree rsambuca. I scanned through this and It's not that clean.... but quite good. Also, I think you have done a fairly good job of organizing it, but you could do a bit better :).

---

### Post by rsambuca on 2007-12-08
I have to strongly disagree with a couple things:

/boot partitions are really not required and often create more problems than they are worth.

fat32 is an antiquated filesystem that is prone to problems, has no journalling, requires constant maintenance, and has file size limitations.  If a shared partition is required, I recommend either ext3 or ntfs.  Both can be read/write from both Windows and linux, using the fs-drivers and ntfs-3g drivers respectively.  Although access times are a bit slower for the non-native file type, the benefits still outweigh the potential problems of FAT32.

---

### Post by zesty on 2007-12-08
> **rsambuca said:**
> I have to strongly disagree with a couple things:

/boot partitions are really not required and often create more problems than they are worth.

fat32 is an antiquated filesystem that is prone to problems, has no journalling, requires constant maintenance, and has file size limitations.  If a shared partition is required, I recommend either ext3 or ntfs.  Both can be read/write from both Windows and linux, using the fs-drivers and ntfs-3g drivers respectively.  Although access times are a bit slower for the non-native file type, the benefits still outweigh the potential problems of FAT32.

Thanks for that!  Really.

There&#347; a lot of info, even in the stickies here, that imply a /boot partition is a good idea.  If that&#347; not the case I hope it gets advertised.

The fat32 filesystem is also recommended in many guides and in the stickies here.  If its time to move on, then great, lets advertise it.

Again, this is a noob guide made by a noob.  I expect some problems, but hope that this or something like it written by someone else can be included in the stickie info.  Anyone should feel welcome to use what Ive written and change it as they see fit.

---

### Post by zesty on 2007-12-12
I have bumped up the suggested max root partition size to 15G.  I downloaded a bunch of games and now my 10G root partition is getting pretty full.

Many PCs come with 250+ gig harddrives.  There's a ton of programs that are free and easy to download so I think a large root partition would be a good idea for many noobs.

---

### Post by kronocyber on 2007-12-12
> **rsambuca said:**
> I have to strongly disagree with a couple things:

/boot partitions are really not required and often create more problems than they are worth.

I keep a /boot partition on hda1 becuase my root "/" partition is on md0
wich is a soft raid0 that my computer dose not like to boot from go fugure.

md0 is striped on hde and hdg wich are plugged in to seperate ide chanels on
my promise ide controler. 

as far as swap gos I have a small swap on hda2 and hdb1 bolth same size.
I set them to the same priority in /ect/fstab hoping to get some performance gain.
hda and hdb are on the same ide cable so I doubt there is any gain from putting
the swap at same prioity but one can hope :confused:

naw in general though Ive found there can be several uses for a boot partition,
but it is generally not necisary unless youre doing somthing weird

---

