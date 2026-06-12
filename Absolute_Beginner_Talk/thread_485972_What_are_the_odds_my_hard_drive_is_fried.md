---
title: "What are the odds my hard drive is fried"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-06-27
Backstory... bought a nice big external usb hard drive. Formatted ext3, added to fstab, mounts at /data/video everything works fine. Never unplug it from the computer at all, its only external because i ran out of ide ports and cant afford the upgrades to get raid goin.

After a few reboots spread throughout a week or two, it starts informing me its mounting ext3 filesystem with errors and forces an fsck. I can handle that, cept it takes FOREVER to fsck a 320gig hard drive. No errors reported except 2.2% non contiguous data (not even sure if thats an error or if its just info it found). Then it lets me continue boot.

Get back into ubuntu... and everything seems to be going well till i try to randomly access a folder on the hard drive... nothing in it... well the info's still there but ls returns an input output error. So im like damn. Oh well, research fsck, ext3 all that jazz, umount the drive, fsck it, everything good but the 2.2% non contiguous again. Any further fsck reports totally clean, so i remount it.

Works fine for a while, untill i go into another folder on the drive (this time a different folder that DID work before) and get the ls input output error and no files displayed again.

Lather rinse repeat, umount, fsck, non contiguous, fsck again, clean, mount, works till another random point in time in another random folder.

I've tried reverting it back to ext2, editing a few options in my fstab (sync instead of async, and whatnot) and still encounter this issue aparently randomly. While it is recoverable from, with the usual umount, fsck, and remount... its very annoying and time consuming to have to unmount a filesystem, fsck 320 gigls of data, and remount the drive just to watch a video or two

So, what are the odds the drive is jacked... IF i could find the space somewhere else, back the files up, delete the partition, reformat it AGAIN, and put the info back, is there a chance it will be more stable... or is it more than likely just going to jack up again??

---

### Post by Seisen on 2007-06-27
How old is the hard drive?

---

### Post by Nythain on 2007-06-27
about 3 weeks

---

### Post by GMachine_24 on 2007-06-27
Hi:

My experience - and please note this is just me not some Linux guru - is that USB works as well on my Linux boxes as does setting a house on fire because it's cold outside. Ok, that probably doesn't make sense but in short, I have never been able to get an external USB hard drive to work with any version of Ubuntu I've tried; with Fedora; I could go on by I think you get the point.

So, I either use firewire drives (which previously were time consuming to configure but the most recent two versions of Ubuntu seem to have adding external firewire hardware down to a true plug-and-play experience). I have somewhere on these forums posted all the stuff I had to do to get firewire drives to work in .... I think it was Ubuntu 5.

The other thing I do is buy a cheap - and I do mean cheap, like $13 - PCI card that bills itself as a RAID device but I just plug up to four hard drives into the card using standard cables and everything works great. Have never had them fail/falter. I do advise buying some of those 5.25 external hard drive cases that you can put your hd in and then install the case into a free 5.25" slot if you have one. If not, I have mine stacked up next to the computer; I use ones with cooling fans and they are easy to swap with another hard drive if you have another compatible plastic chassis.

This is probably more than you wanted to know. I hope it helps.

gm

---

### Post by moredhel on 2007-06-27
saying that, every single one of my harddrive comes up with erros from fsck, even one in a brand new laptop with no OS installed or anything :\

---

### Post by GMachine_24 on 2007-06-27
I do not have problems with fsck and false positives or whatever you want to call them. I have had to force an fsck check on one drive recently - the first time I've had to - and it stopped at all the errors, offered to fix them, I said yes and pretty soon the drive was good.

gm

p.s. the previous poster brought up a good point - if you have another Linux box you can connect your USB drive to that would be a good test. I can't remember if you tried this.

---

### Post by Nythain on 2007-06-28
hmmm... bout to bust this thing open and see if i can connect it ide... who needs a dvd drive for a while...

update on the problem. It appears to just jack up after staying mounted for a while, and the random directory appears to be the first directory i try to access after not accessing it for a while... a simple umount and mount sans fsck fixes the problem, so im wondering if it just has to do with the drive powering down while not actually being accessed or something, then something going wonky when it starts back up... i know that doesnt make much sense, but its about all i got at the moment

---

### Post by ginestre on 2007-06-28
> **GMachine_24 said:**
> Hi:

 I have never been able to get an external USB hard drive to work with any version of Ubuntu I've tried; with Fedora; I could go on by I think you get the point.

gm

My western digital MyBook 320 works straight out of the box on 3 differnt PCs with Feisty.... I just move it around from office to home to beach house (that's why I bought it)

---

### Post by Swampfox on 2007-07-02
> **ginestre said:**
> My western digital MyBook 320 works straight out of the box on 3 differnt PCs with Feisty.... I just move it around from office to home to beach house (that's why I bought it)

I also have 2 different USB drives that work perfect without any configuration whatsoever.  I plug them in and an icon appears on my desktop.  

You might try plugging it into a different machine/laptop and see if it works to your liking.  If it works then it most likely isn't the drive.  If you still have issues with it then I would call whomever made your drive, send it in for repair or a brand new one.

---

