---
title: "another grub issue (karmic mbp-3.1)"
date: 2010-07-29
forum: Apple Hardware Users
---

### Post by josiano on 2010-07-29
hello

since yesterday morning, my ubuntu karmic (pure:dyne) won't boot anymore, I'm stuck on GRUB_ on my macbook pro (santa rosa).
(had this issue some months ago but re-installing grub fixed it last time, this time not)

I spent the last 2 days googling around and found *a lot* of related threads but none really helped:
I tried unsuccessfully to swap my MBR (on /dev/sda), re-install grub (4 times), I eventually re-installed ubuntu but I still have the same issue, stuck on 'grub_' (before the menu).
that was not an easy task because my stoopid mac only boots from cd/dvd 1 time on 100 (no jokes) :|

I have no idea of why I have this problem suddenly re-appear but I guess it might be related to my GPT/MBR hybrid partition. (if you look below***, the fact that /dev/sda3 (which is where I have ubuntu) is seen as EFI FAT is weird to me... also the 1st partition doesn't start on the same block on GPT and MBR.. dunno if that's normal)

reformatting the drive and reinstalling osx and ubuntu is not an option right now  because I'm too broke to buy another HDD to backup everything.

any hints from you gurus is much appreciated.

here is my partition table (in case):

```

Current GPT partition table:
#    Start LBA    End LBA      Type
1    40           409639       EFI System (FAT)
2    409640       149002874    Mac OS X HFS+
3    149002875    158770394    EFI System (FAT) ***(uh???)
4    158770395    160923104    Linux Swap
5    160923105    234436544    Basic Data

Current MBR partition table:
# A  Start LBA    End LBA      Type
1    1            409639       EE  EFI Protective
2    409640       149002874    AF  Mac OS X HFS+
3 *  149002875    158770394    83  Linux
4    158770395    160923104    82  Linux swap / Solaris

Status: Tables are synchronized, no need to sync. 

```

thanks,
_yvan

---

### Post by conundrumx on 2010-07-29
Well, you say wiping everything isn't an option, so here's what I'd do (other than wipe everything and start from scratch.)

Clean out all the non OSX partitions.  Every single one.  I'd probably expand the HFS+ partition just to be sure.  
Install rEFIt (if you haven't already, I assume you have).  
Use Boot Camp Assistant to resize your disk, but select "Quit" when done, not "Reboot and Install."  
Boot up Ubuntu and use G/parted to make free space look how you want the Linux section to look.  
Start the installer (any reason you're using Karmic instead of Lucid?), and specify "advanced" partitioning.
Make sure and reformat the section of the drive you're using as /, and don't forget swap.
When you reach the end of the installer, select "Advanced" and have Ubuntu install GRUB on the same partition (say, /dev/sda4) as /.

---

### Post by josiano on 2010-07-30
so you think that my ext3 partitions are messed up ?
yesterday, last time that I re-installed ubuntu, I formatted again those partitions already...

I'd love to understand why it does not boot...

> any reason you're using Karmic instead of Lucid?
I use pure:dyne (last version based on karmic), and I had very bad graphic troubles with Lucid

cheers,
_yvan

---

### Post by conundrumx on 2010-07-30
> **josiano said:**
> so you think that my ext3 partitions are messed up ?
yesterday, last time that I re-installed ubuntu, I formatted again those partitions already...

I think your MBR and/or GRUB and/or gremlins are the source of your problem.  Instead of trying to troubleshoot the exact problem, since you already reinstalled Ubuntu once, I figured another time couldn't hurt.  ;)

---

### Post by josiano on 2010-07-31
okay, found the time today to delete all ext3 and swap partitions with parted, then grow hfs+ to fill out all remaining disk space with diskutil.

I installed ubuntu again (this time without a separate HOME partition so gpt is happy with my 4 partitions), installed grub on /dev/sda3 (because of refit)...

same problem.
I choose linux in refit, I have a blinking cursor that quickly disapears, then few seconds black screen, then stuck on 'grub_'... and still no menu.

strangely, after installing ubuntu, refit says that partitions are already synced.

I had the exact same problem last year with the same macbook pro, gave up for 6 months. then I found a thread with a solution but this time I cannot find anything that solves it :/

any hint much appreciated

cheers,
_y

---

### Post by josiano on 2010-09-18
bump

sorry for digging this out but now my older computer is fxckd up so I badly need my ubuntu on osx back...

just a side note, in refit I see now 3 penguins ... none of them boot. (still stuck at grub_)

thanks
_y

---

### Post by josiano on 2010-09-19
I managed to repair this with superGrub2disk =)

booting with it fixed my MBR.
now I choose linux from EFI (instead of /dev/sdX) and it works !

cheers,
_y

---

