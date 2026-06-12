---
title: "Grub dead end"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by akumax on 2006-12-03
Hi, I'm new (obviously), my goal is to get XPmce and Kubuntu to dual boot. I tried _first _to install Kunbuntu to my _seperate_ slave drive (Xp being on the master drive) but I got nothing but headaches. So I removed the XP drive completely and installed Kubuntu again on the secondary drive (this time being the only drive, set to Master). This drive still has an NTFS partition as the first partition with all my storage data from windows. My devoted free space is after the partition. This is where I installed Kubuntu. I remember I chose grub to install on (hd0) during my first attempts (while XP drive was still the master) and so I figured on the second attempt (with the XP drive removed) that I would chose to install grub on (hd0,1). What I am getting now when I boot is:

Grub loading stage 2...

(then I see)

[Minimal bash-like line editing is supported. blah blah blah..]
Grub>

At this point I am clueless. My goal at this point is to simply get the Kubuntu installation, on this singular drive (with an NTFS partition as the first partition), to boot up. I anticipate moving forward after that to get Xp added into the boot mix later.

Thanks for any help =)

---

### Post by Sef on 2006-12-03
Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").
 It talks about Ubuntu, but Kubuntu should work the same way.

---

### Post by smile_sunshine on 2006-12-03
by the way if you are going to set the drive back to slave and put the windows xp one in as master you will need to alter the /etc/fstab file so it points to the right drive - (either from hda to hdb or from sda to sdb)

:)

---

