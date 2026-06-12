---
title: "Formating 4gb sdhc card"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-02-15
is it possible to format my 4gb sdhc card from the fat32 system to fat16. I have heard some people have done this and i was wondering how.

---

### Post by Het Irv on 2008-02-15
I don't know why you would want to, but have you tried using g-parted on the live CD?

---

### Post by intense.ego on 2008-02-15
I got it working using my XP computer, but it still didn't work with my phone or my M3 DS Simply. Is it possible to somehow downgrade a 4gb micro sdhc card into a 2gb micro sd card?

---

### Post by intense.ego on 2008-02-16
bump. anyone?

---

### Post by Het Irv on 2008-02-18
You could try to put a partition on it but I can't think of anything other than that.

---

### Post by Neobuntu on 2008-02-27
I guess there is no way to format a HC flash to be non-HC.

M3 and the R4 do not do the "HC"(High Capacity spec = 4GB and up) of MicroSD**HC** flash. Whether they do an older **non** HC(SD 2.0 spec) 4GB MicroSD I'm not sure. I doubt it. 

You definitely require an HC reader for an HC flash. They are set to not work otherwise. Although, any HC reader will read smaller capacity (2gb or less) SD (non HC) flash.

DSTT and the Evo DS carts do HC. MicroSDHC, that is.

Get a 2GB MicroSD for the M3

Get a DSTT (from your country not HK) and another MicroSDHC reader (the DSTT included one stinks, and may corrupt your drive.)

Note that if you get OVER a 4GB now, the DSTT's OS will be to slow (for my taste). Because **more than** 4GB, would require FAT32 only; for one partition. I am hoping the NDSTT.com team will fix the slowness with FAT32 (more than 4GB).

VFAT16 (FAT) is faster than VFAT32 (FAT32). Use VFAT16 on smaller (4GB or less) flash, it's the norm. Use directories with FAT16, to keep within it's root file count limit. You will still have long files names.

The old limit was FAT16 (non VFAT16) 2GB.

Some devices only do FAT, some only 2GB (or whatever their device OS does).
> sudo umount /dev/sdx1

sudo mkfs.vfat -c -F 16 /dev/sdx1 to format VFAT16; With x: as your flash.

There is only one default VFAT16 allocation that yields 4GB. So don't worry about that.

Other Win XP formatters will default to FAT32. Use the above command or something like HP's flash format utility (Or let your device do it).

XP did not work for me, with an HC drive, even with MS SDHC hot fix patches. Kubuntu does great.

FYI: Flash uses a SCSI technique to become mass storage. That's why they show up as /dev/sdx1. "s" for SCSI. "x" being it's drive letter (change tis to yours). Use > sudo fdisk -l...(that's with an L but lower case) to **l**ist it.

Many people say, do not defrag flash drives. They do not need it. They don't spin (but you could backup and rewrite them). Defrag and other HD tools may very well corrupt your Flash drive!

Do not use FAT file sorters that require un-mounting your Flash. Foldersort does a fine job and while mounted; via simple, fast, move techniques. I recommend checking your Flash drive (FAT system) FIRST (see below).

Do not turn off your device, while it may be writing. You will corrupt your FAT.

You can use something like > sudo dosfsck -ar /dev/sdx1...depending on your drive letter, in place of "x", to check and/or fix FAT.

I can't be held responsible if you format the wrong drive. Have TWO backups and be careful. :)

Let me know how you like Metroid Prime Hunters.

---

### Post by Neobuntu on 2008-04-04
Hmmm, rumor has it that changing format to VFAT32 or changing to VFAT16 can move the actual point where files are stored (FAT32 having bigger FATs) and the could "miss align" how your OS virtually "sees" the drive with the internal Flash (bigger) pages. 

Also, standard Windows XP formating messes up Flash media as it formats it like a floppy (no partition at all) not to mention as FAT32 when it was FAT16.

Do not remove the empty slack space before Flash partitions. Do not "defrag" Flash. Do not use any hard drive tool on Flash drives.

If it's an SDHC Flash, format it (if you have to) in a SDHC camera. Use a quality SDHC reader and try another one if you have problems.

---

