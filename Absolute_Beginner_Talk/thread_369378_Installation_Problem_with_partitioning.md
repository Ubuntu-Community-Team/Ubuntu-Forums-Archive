---
title: "Installation Problem with partitioning"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by drusepth on 2007-02-24
Hey, I decided to set up a dual boot with Windows and Ubuntu on my laptop.  Anyways, I download the ubuntu iso from ubuntu.com and boot to it.  Everything works fine, and I get to the desktop, where I open the Install application.  

I easily work through it until I get to step 5 of 6: Prepare disk space.  This is what is displayed:

Prepare disk space
 How do you want to partition the disk?
 (bubble) Manually edit partition table.

       [Cancel]  [Back] [Forward]

So, I click Manually edit partition table and click Forward to proceed.  On this next screen, it tells me that No devices are detected.  I'm not sure what to do from here.

Also, I have an SD Card slot in my laptop.  I can insert an SD Card, and on the first Prepare disk space screen, it will recognise it.
 How do you want to partition the disk?
 (bubble) Erase entire disk: /dev/mmcblk0 - 255.1 MB Unknown
 (bubble) Manually edit partition table.

After this, I choose manually edit the partition table, and it will only recognise my SD card.  Any help is greatly appreciated, and I'll try to answer all questions you ask to help you help me.

This is my first time with Unix/Linux.  I've used it some before, on other's computers and on LiveCDs, but I've never installed it.

---

### Post by hyper_ch on 2007-02-24
Please download the alternate install cd and try to install from it.... the live-cd sometimes has a few problems and the alternate install cd may help in this case.

If the alternate install cd doesn't detect your existing drives, then you can do repartitioning from windows with a tool such as PartitionMagic (not free)... however before you twinkle around with partitioning and stuff make sure you **have backups**.

Also before resizing you should first defragment your drive 2-3 times in windows. This will greatly speed up the resizing.

---

### Post by drusepth on 2007-02-24
I'm sorry, I forgot to mention a few things.  First, I've tried this three times now.  Once with a CD that was sent to my brother, once with an iso my brother downloaded, and once with this iso I downloaded.  The version of Ubuntu I'm trying to install is the newest one, version 6.10.  The link is [http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease), and to get to the download I chose, it's North America>United States>Ftp-mirror.internap.com>CD Image for desktop and laptop PCs.

[quote="hyper_ch"]Please download the alternate install cd and try to install from it.... the live-cd sometimes has a few problems and the alternate install cd may help in this case.
[/quote]
What do you mean by the alternate install cd?  Do you mean download a different version, or a different mirror, or the Other Installation options?  I didn't think the Other Installation options choice was right for me, because it says "including 64 bit CD images, server installation CDs and alternative installation methods for OEM computers and computers with less than 192MB RAM"

Thanks for reminding me about the backups.  I backed my computer up the last time I tried installing Ubuntu, but that was almost a month ago and I've done a lot since then.

---

### Post by i.am.canadian on 2007-02-24
Hi there,

When he is referring to the alternate cd he means the one for computers with less than 192mb of ram.  This cd won't boot to a desk top, and for whatever reason, seems to do a better job of detecting hard ware.  The name of the ISO file should say something like "i386-alternative."  If you try burning that to disk and installing for it you might be able to detect your hardware better.  I hope that clears some things up for you.

Cheers.

---

### Post by drusepth on 2007-02-24
Thanks i.am.canadian, I'm trying that now.  I just ran the Integrity Test on the cd, and it failed.  "The ./pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb file failed the MD5 checksum verification.  Your CD-ROM or this file may have been corrupted."

I looked on the ubuntu site for a MD5 checksum download, and can't seem to find one.  Is this supposed to be included, or do you have to download it seperately?  Or is it just checking the MD5 against that file?

---

### Post by i.am.canadian on 2007-02-26
Hi again,

If you go to the server where you downloaded it from (I'm not sure which one you are using, but I just checked the Austria one) and it should have a file called something like "MD5SUMS" without any extension.  

I just clicked on it and it opened up a page (I'm using firefox if that matters) and you can just copy and paste the MD5SUM that corresponds with your iso (alternate i386 for example).  

However, to actually check the file against that MD5SUM you are going to have to go to the terminal (as far as I know).  I've never done this myself on linux (I did it from windows before I made the jump) you can find out more information here [http://www.openoffice.org/dev_docs/using_md5sums.html]("http://www.openoffice.org/dev_docs/using_md5sums.html").  Its a page for openoffice but the information applies.  If you don't want to use the FF extension, scroll to the bottom.

If the check says that your download is corrupted, the sad reality is that it might be.  In which case, you'll have to download a new copy.  If, on the other hand, it is not the iso but the cd, try burning it at a lower speed.

I hope this helps.

Cheers.

---

