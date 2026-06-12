---
title: "File server with software raid 5 -&gt; how?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by tuckie on 2007-04-12
The final pieces for my new fileserver (4, 500GB drives and an athlon x2) are coming in on Monday, I figured that I would get your guys opinions how exactly I should tackle this.  First of all, I have been able to figure out that I need to use mdadm in order to build the array, but have yet to find an ideal guide for doing this.  I'm also confused as to how/if lvm comes into play.  Which filesystem would you guys reccomend for the server?  I plan on having most of the space taken up with dvd rips, avi's, mp3s, as well as some various document and photo backups.  Any other tips for my first linux fileserver would be greatly appreciated. :D

---

### Post by rbprogrammer on 2007-04-12
not an expert on this, but my choice would of been ext3..

if you haven't already, you could check out: 
[http://en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems") 

although, sometimes i don't trust the content on wikipedia considering almost anyone can post "facts"..

---

### Post by george29 on 2007-04-12
[http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

some guides i found with google...

---

### Post by tuckie on 2007-04-12
oh, also, will this allow me to expand to more hard drives (and expand the partitions) in the future?  And how does linux handle a failed drive in a RAID array?

---

### Post by george29 on 2007-04-12
you ought to look at the following 

[http://www.freenas.org/](http://www.freenas.org/)

[http://www.freenas.org/downloads/docs/user-docs/FreeNAS-SUG.pdf](http://www.freenas.org/downloads/docs/user-docs/FreeNAS-SUG.pdf)

it's a BSD distro specifically to act as a network attached storage (NAS) raid server. 


_**Very important - this is a stand alone OS - you can't dual boot a computer running freeNAS**_

---

### Post by tuckie on 2007-04-13
I've thought about it, but freenas doesn't offer nearly the flexibility that I need.  I'll probably use it as a torrent client, maybe use it as the dvd ripper, and eventually turn it into a mythtv backend.

---

### Post by tommi-fi on 2007-04-13
[http://www.evileyez.org/quick-and-dirty-linux-software-raid5/](http://www.evileyez.org/quick-and-dirty-linux-software-raid5/)

Address says it all..

EDIT

and growing raid5 array [http://scotgate.org/?p=107](http://scotgate.org/?p=107)

---

### Post by tuckie on 2007-04-13
whats with this: > Just in case there is Ubuntu readers, they need to know that RAID5 array reshaping is disabled in the stock kernels, giving an &#8220;invalid argument&#8221; error when trying to grow the array. So they need to compile a custom kernel and enable the option CONFIG_MD_RAID5_RESHAPE=y in the .config file. Note that kernel 2.6.17 or above is required.

---

### Post by tuckie on 2007-04-15
anyone?

---

### Post by freebird54 on 2007-04-15
I don't know enough myself, but here is a thread with some knowledgeable people in it that you can ask!  :)

[http://ubuntuforums.org/showthread.php?t=408916](http://ubuntuforums.org/showthread.php?t=408916)

It even has a little discussion on LVM and where it fits.  Hope it helps!

---

### Post by RoboJ1M on 2007-04-16
Two documents I've found and will be partially following (ignoring the Gentoo stuff at the end) are:

[http://gentoo-wiki.com/Installing_on_LVM2_And_Raid5]("http://gentoo-wiki.com/Installing_on_LVM2_And_Raid5")
[http://gentoo-wiki.com/Resize_LVM2_on_RAID5]("http://gentoo-wiki.com/Resize_LVM2_on_RAID5")

My machine will be initially based on 3 Western Digital 500GB RAID Edition ATA drives, with two more to follow when I run out of space.

Regards,

J1M.

---

### Post by zaziork on 2007-05-08
> **tuckie said:**
>  Which filesystem would you guys reccomend for the server?  I plan on having most of the space taken up with dvd rips, avi's, mp3s, as well as some various document and photo backups.  Any other tips for my first linux fileserver would be greatly appreciated. :D

I've just got my system up and running with 3x 500GB Sata2 drives running in RAID 5 on LVM(2). I'm playing around with MythTV at the mo. Seems to be working a treat. As far as file system, I'm using XFS, as that allows greater flexibility in terms of resizing the LVM partitions in future. Hope you're getting on OK building your system.

---

