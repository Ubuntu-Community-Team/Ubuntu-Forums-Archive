---
title: "Ubuntu will not install"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by qquag on 2006-11-01
I Got the nerve up and was going to install ubuntu on my laptop.  It boots up just fine on the live cd and runs great, all my things are working (wireless, bluetooth, Ect.)  However when I try to do a install I get to the point where it ask me to partion the drive I hit accept on the default.  Some where around 50% only 1/8 hdd used.  and it locks up done this like 3 times.   Each time I would reboot and try again.   I then thought I would try the partion my self and I went into the qtparted v0.4.5-cvs I chose to resize partion and hit accept and I keep getting a error "Opening 'dev/sda1' as NTFS failed: operation not supported".   

More info Just incase you need it.   Laptop is a Dell Latitude D510 Has a 80 Gig HDD Running the new Ubuntu.   

qtparted reports   /dev/sda1    ntfs     active    74.53GB   13.28 used   .03MB  End 74.53GB

---

### Post by %hMa@?b&lt;C on 2006-11-01
have you tried it from the alternate cd. some people have had that problem, and that seems to fix it.

---

### Post by curtisf14 on 2006-11-01
First, make sure that the CD you downloaded does not have any errors on it.  I've heard of people's installations freezing up if the downloaded CD did not download correctly.  You can do this by checking the md5 checksum of the downloaded file with a checksum provided on the download page (there should be instructions on how to do this).

Also, whenever I need to do an install by making a new partition, I use GParted to make the partition I want before doing the Ubuntu installation.   I've never tried installing Ubuntu on a NTFS formatted drive, as I know that Linux and NTFS don't mix very well, so that could be an issue to.  Try using GParted to resize your partition first (but of course, back up all your stuff before doing this).

If none of this helps, just post again any issues you had on the second round.  :-)

---

### Post by qquag on 2006-11-01
Not for sure where to get the alternate cd.  I did test the Cd and it showed there were no errors.   I have tried both ways to partition the drive by the automated with the install and by the GParted to resize the partition.

---

### Post by raqball on 2006-11-01
Are you trying to insall it as NTSF or ext3?

---

### Post by caravel on 2006-11-01
I had this problem when I tried to reinstall Kubuntu after having Fedora installed.  gparted seems to have problems removing old partitions.  I used fdisk from the livecd to remove the old partitions.  That may not be the problem though.  Did you check the disk for errors from the livecd boot menu?

---

### Post by fatneck on 2006-11-01
This has happened to me several times trying to get Ubuntu dual booting with XP. Eventually I booted back into XP and in the disk management just deleted the rest of the partitions that various linux's (linuxes? linuxi?) had been on.

This screwed up the MBR and I couldn't boot into windows but using the recovery CD and fixmbr and/or fix boot command it reset the MBR and was then just a windows machine with half a hard drive unnacounted for.

Then when I ran the Live CD again, I was able to use the builtin partitioner on Ubuntu to make the 3 partitions and it was fine. It also has its own GRUB so I have the choice of Ubuntu or XP at boot now.

Hope this helps, plenty more questions from me will soon follow for you good people, oh yes!

---

### Post by Ocxic on 2006-11-01
you could always use the live CD to create/format your partitons then you wouldn't have to worry about it, just select you mount points and go.

---

### Post by NeoGreen on 2006-11-01
I had the same problem.  What I had to do was to to reburn my Ubuntu CD again using a slower speed.  On the first one I burned and used as a Live CD it worked fine but when I tried to install it.  It would stop have way.  You may want to download a new copy then burn it at a slow speed.

---

