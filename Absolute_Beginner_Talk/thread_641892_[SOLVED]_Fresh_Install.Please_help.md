---
title: "[SOLVED] Fresh Install.Please help"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by linux phreak on 2007-12-16
Hi friends.Im trying to install ubuntu 7.10 on my system by wiping out xp.I booted from live CD and clicked the install button.Then on the Prepare disk space i see my two hard drives under "Guided" option. One is 40 gb and other is 160 gb.I have Installed xp on the 40 gb drive while the other is used for storage.I wanna know that if i choose SCSI1(0,0,0)(sda) 41.1 drive, will it wipe data on my second hard drive(SCSI1(0,1,0) 160.I need the data so i dont want to loose it. please help.:)

---

### Post by thelatinist on 2007-12-16
These are separate physical drives, right?  If so, it should only format the drive that you select.

---

### Post by linux phreak on 2007-12-16
Thank you for the reply.These are separate drives.But will the second disk be usable in ubuntu?after the istallation of ubuntu ie access its contents(play music,video) etc.Will there be any problems during bootup.Thanks

---

### Post by tekwerx on 2007-12-16
> **linux phreak said:**
> Thank you for the reply.These are separate drives.But will the second disk be usable in ubuntu?after the istallation of ubuntu ie access its contents(play music,video) etc.Will there be any problems during bootup.Thanks

That depends on the filesystem of the drive.  If its FAT32, yeah, it'll be seen right off the bat.  If its NTFS, you'll have to do some light work to get it to be useable.  (Outdated info maybe...Ive not used Windows for a while, so Ive not had to mess with NTFS, but last I knew, it wasnt supported unless you added it yourself.)

---

### Post by linux phreak on 2007-12-16
But the second drive is NTFS.What should i do to get ubuntu recognize it without wiping it clean.Im a beginner and i liked ubuntu very much and also this community.

---

### Post by tekwerx on 2007-12-16
> **linux phreak said:**
> But the second drive is NTFS.What should i do to get ubuntu recognize it without wiping it clean.Im a beginner and i liked ubuntu very much and also this community.

Dont wipe it, there's no need.  Im not up to date on the exact howto for it, but there is a way to enable Ubuntu to see the drive and use it.  Search the forums for NTFS, and look through some of the posts.  Im confident youll find your answers.

---

### Post by karrotcake on 2007-12-16
Ubuntu will recognise the filesystem, and should automatically create a link on your desktop to your NTFS partition. It wont allow you to write to the partition though; for that you'll need to look into using the ntfs-3g package.

---

### Post by linux phreak on 2007-12-16
Thank you so much.I will search for it.

---

### Post by linux phreak on 2007-12-16
So the data will be intact right?.Then its time to give xp the boot

---

### Post by thelatinist on 2007-12-16
> **linux phreak said:**
> So the data will be intact right?.Then its time to give xp the boot

Yes.

---

### Post by jimrz on 2007-12-16
if you are installing gutsy 7.10 ntfs read/write support will be there "out of the box", no longer need to add it manually.

---

