---
title: "Hard drive problem"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by kramer3d on 2005-08-07
Hmm. Well Ive got a little problem. My current HD (40gb) has XP on it. When I add my new HD, I want my current HD to have ubuntu and the new one to have XP.

Does anyone how I can get this done?

---

### Post by aysiu on 2005-08-07
Yes.

1. Back up your Windows data.
2. Install XP on the new drive.
3. Put the Windows data back there.
4. Install Ubuntu on the old drive.
5. When asked if you want to install Grub to the MBR, say "yes."

Just so you know, though, XP is typically an NTFS filesystem by default. Linux can read from NTFS, but it can't write to it. You may want to have a middle partition (FAT32) that both Windows and Linux can read from and write to.

Actually, if you ask me, your best bet is to have one drive (the smaller one) that has both OSes (applications and settings) on it and the other drive (the bigger one) formatted as FAT32 to store all your files.

---

### Post by kramer3d on 2005-08-07
[QUOTE=aysiu]Yes.

1. Back up your Windows data.
2. Install XP on the new drive.
3. Put the Windows data back there.
4. Install Ubuntu on the old drive.
5. When asked if you want to install Grub to the MBR, say "yes."

Just so you know, though, XP is typically an NTFS filesystem by default. Linux can read from NTFS, but it can't write to it. You may want to have a middle partition (FAT32) that both Windows and Linux can read from and write to.

Actually, if you ask me, your best bet is to have one drive (the smaller one) that has both OSes (applications and settings) on it and the other drive (the bigger one) formatted as FAT32 to store all your files.[/QUOTE]
Hmm... so Linux can read and write to FAT32?

I want to make the current HD complete Linux and the new one complete Windows.
So how can I make the current HD Fat32? (Im planning to leave the new one NTFS)

---

### Post by aysiu on 2005-08-07
[QUOTE=kramer3d]Hmm... so Linux can read and write to FAT32?[/quote] Linux can read and write files (music, pictures, documents, webpages, videos, etc.) from and to FAT32, but the actual Linux system should be installed on its native format (EXT3).

> 
I want to make the current HD complete Linux and the new one complete Windows.
So how can I make the current HD Fat32? (Im planning to leave the new one NTFS) Okay, so the new hard drive will be NTFS Windows XP. That's easy. XP will do that by default. When you install Ubuntu, you'll be asked to partition the drive. You should do the following:

6 GB of EXT3 for /
twice the RAM of swap for the swap partition
all the rest for the FAT32 partition and mount it at /windows

Do you know much about partitioning? Ubuntu's partitioning tool is text-only, but it should work fine. If you want a graphical partitioner, you can pay for Partition Magic, or you can use QTParted (included with Knoppix and Mepis) or DiskDrake (included with Mandriva). I personally think DiskDrake is the most reliable, but it's up to you.

---

### Post by kramer3d on 2005-08-08
Actually this is the first time I will be partitioning anything in my life. I will look into partition magic and the other softwares  ;-) 
> 6 GB of EXT3 for /
twice the RAM of swap for the swap partition
all the rest for the FAT32 partition and mount it at /windows

so when should I do this part? Before installing Linux or during?

---

