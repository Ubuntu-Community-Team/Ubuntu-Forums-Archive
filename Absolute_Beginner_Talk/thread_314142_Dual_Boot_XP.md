---
title: "Dual Boot XP"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by scottsanpedro on 2006-12-07
Hello to all...
I have programmes for finance's etc on my XP configured laptop so need to keep some space for XP when dual booting, also couple of games. I have 40gb drive, and want to keep about 15gb for XP. Right now I have 1 partion for 40gb and its NTFS. I have partion magic currently running on XP and wanted to know if I could set the partion up through XP before running Ubuntu.
I have also read that there seems to be better ways to organise the partions for Ubuntu, i.e. Ram swap area, another area for /home so if I need to re-install all my settings are there etc? How would I do that.
I know there are alot of HOWTO's around but wanted some info on the best way to do this.
Many thanks Scott

---

### Post by robinl on 2006-12-07
Ubuntu installation can resize your NTFS partitions itself so you won't need partition magic. However it is still recommended to back up your valuable information just in case.

---

### Post by drphilngood on 2006-12-07
> **scottsanpedro said:**
> Hello to all...
I have programmes for finance's etc on my XP configured laptop so need to keep some space for XP when dual booting, also couple of games. I have 40gb drive, and want to keep about 15gb for XP. Right now I have 1 partion for 40gb and its NTFS. I have partion magic currently running on XP and wanted to know if I could set the partion up through XP before running Ubuntu.
I have also read that there seems to be better ways to organise the partions for Ubuntu, i.e. Ram swap area, another area for /home so if I need to re-install all my settings are there etc? How would I do that.
I know there are alot of HOWTO's around but wanted some info on the best way to do this.
Many thanks Scott

Hi Scott,

I´m not familiar with ¨partition magic¨ but here is how I did mine when I had XP by making use of the great partitioning program in the Ubuntu Alternate Installer CD.

* Backup all important data.

* Download the ¨alternate installer CD¨, burn as iso to CD.

* Set bios to boot from CD and then boot from CD.

* Shrink XP partition to desired size(you said fifteen gig).

* Create OS partition out of newly freed space.  I use ReiserFS and made mine twenty gig but five is sufficient(check distro specs).  Mount point is ¨/¨.

* Create swap partition.  Accepted policy is (swap should be equal to twice your ram).

* Create home partition(I use ext3 for this).  Mount point is ¨/home¨.  This is where you will be storing your data so use the rest of your free HDD space here.  Alternatively, some(myself included) like to make a partition for just personal data.  Therefore, instead of using all of the leftover freed space on the home partition, I divide the leftover freed space between my home partition and a partition I create called ¨my files¨(mount point is /home/user name/my files).  This keeps my data files separate from all those ¨user settings¨ files.


That´s it, hope this is what you were looking for.

Good luck!

edit:
Thought you might like to see this link:

[Recommended Partitioning Scheme]("http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apas03.html")

---

### Post by scottsanpedro on 2006-12-07
thats brillant. Thanks so much.
I will check this info out once I'm home. Many thanks again. Scott

---

### Post by Sef on 2006-12-07
Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") for a pictoral tutorial on how to dual boot.

---

