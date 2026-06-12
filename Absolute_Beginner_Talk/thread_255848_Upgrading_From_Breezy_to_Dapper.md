---
title: "Upgrading From Breezy to Dapper"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Millie on 2006-09-12
Hello

I have just ordered some dapper disks via shipit. Will I be able to upgrade from Breezy using these or do I need some 'other' dapper disks?

Thanks

---

### Post by welshboy on 2006-09-12
Hi there, 

I upgraded by downloading the ISO image, and ran it.  I thought I downloaded the wrong version initially as it went to a Live desktop, however it was the right one.  You shouldn't need any other CD other than the Ubuntu CD, I certainly didn't.

In terms of upgrading, are you intending to have a dual boot system with two seperate versions of Linux?  Of not, I would recomend that you back up your data first.  I read in a book by Kier Thomas that Ubuntu partitioner worked out what space was used, and the adjusted the disk accordingly.  I'm not sure if this applies to windows only, or will it do it for linux too.  Someone with more experience could help you more than me.

When I upgraded, I backed up my files and just installed the CD.  

Hope that jumble load of gunk helps :confused:

---

### Post by demonoid on 2006-09-12
sudo apt-get dist-upgrade

---

### Post by nudnik on 2006-09-12
I would reccomend backing up your personal data and doing a fresh install, but that is merely my opinion.

---

### Post by Millie on 2006-09-22
I got my dapper disks yesterday (ubuntu and kubuntu)

when I inserted either of the disks into the CDROM drive, the update manager recognised that there were some updates - about 6 packages, of which only 3 could be installed.

It recommended I run either apt-get dist-upgrade or synaptic 'smart update'. I tried both and whilst 3 of the packages were updated, I could have expected far more packages to be updated e.g. KDE

I'm trying not to go to the length of reinstalling it because my I'm worried it will splat my /home partition.

Are these the 'wrong' disks?](*,)

---

### Post by Perfect Storm on 2006-09-22
It's a good idea to disable unofficial sources in the sourcelist while doing a dist upgrade.

Also if you have alot of compiled stuff on your current ubuntu version you might run into complications.

---

### Post by Millie on 2006-09-22
I have a vanilla Hoary install, with a Breezy upgrade. I'm not trying to upgrade to Dapper.

I don't have any compiled stuff at all.

In source.list I added something like

deb file:/media/cdrecorder dapper main restricted 

Any ideas?

---

### Post by Millie on 2006-09-22
Sorry that last should read, 

I have a vanilla Hoary install, with a Breezy upgrade. I'm now trying to upgrade to Dapper.

I don't have any compiled stuff at all.

In source.list I added something like

deb file:/media/cdrecorder dapper main restricted

Any ideas?

---

### Post by Sef on 2006-09-22
> In source.list I added something like

deb file:/media/cdrecorder dapper main restricted

Any ideas?

To comment out that line, just put a pound sign (#) in front of the line.

It should look like this:

#deb file:/media/cdrecorder dapper main restricted

then it will be ignored.

---

### Post by Millie on 2006-09-22
I put that line in because when I tried to use synaptic, it would unmount the cd, and then constanly prompt me to insert a cd into the drive - because it had failed to mount the cd. I suspect that this is because there isn't an entry in /etc/fstab. So I decided to manually put in a reference to the dapper CD using

deb file: ...etc

rather than leaving 

deb cdrom:[ ..... ]

are you saying that synaptic would be able to auto mount the cd is I added the appropriate line to /etc/fstab?

---

