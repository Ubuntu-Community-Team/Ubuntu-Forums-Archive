---
title: "[SOLVED] Drive full erro, but it is not"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by .nedberg on 2008-02-29
Hi

I have a 128MB Micro SD card in an SD adapter. I want to copy 91MBs of image to the card. I put the card into my card reader and drag the files over. But it stops at about 84MB claiming the drive is full. Copying via command line gives (translated from Norwegian):
```

cp: can not create temporary file «/media/CANON_DC/2008-02-24_14.38.28-000022.jpg»: No space left on device

```
for each of the files not transferred.

df- h gives
```

/dev/sdb1             121M   85M   36M  71% /media/CANON_DC

```

So there is room for the last files, but I can not get them over to the card.

Any ideas?

---

### Post by ByteJuggler on 2008-02-29
can you post just "df /dev/sdb1"

My guess is that the disk is full due to the disk being likely formatted as FAT, which means it's using overly large blocks and so is very wastefull when storing many files smaller than the blocksize, thus losing a lot of space to "slack."  df without the -h will tell you the block size, if I remember correctly.

To count the number of files on the disk, you can use
```
sudo find /place/where/drive/is/mounted | wc -l
```

Replace "/place/where/drive/is/mounted" with the mount path.

---

### Post by jeffus_il on 2008-02-29
Have you looked for hidden files and .Trash  folders? What file system is on the drive? 
```
parted  /dev/sdb1

```then 
```
p
```
may give some useful information.

---

### Post by .nedberg on 2008-02-29
The drive is indeed FAT (FAT-16) formated. The copy operation stops at 170 files, all of size 350-450kB. There are no hidden files on the drive.

```

df /dev/sdb
Filesystem           1K-blocks      Used Available Use% Mounted on
udev                   1038144       108   1038036   1% /dev

```

---

### Post by .nedberg on 2008-02-29
parted gives:

Disk /dev/sdb1: 126MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End    Size   File system  Flags
 1      0,00kB  126MB  126MB  fat16

---

### Post by ByteJuggler on 2008-02-29
OK, sorry my ideal with df without the -h wasn't actually useful as it doesn't tell you the cluster size, my mistake.  However, your other output does help.  

FAT16 uses 16bits for the block number, meaning you can have up to 65536 data blocks max, on your partition.  For a 128MB disk, this means that each block is therefore 128*1024*1024/65536 =2048 bytes.  Which pretty much blows my original idea out of the water. 

Are you copying the files onto the root of the drive?  (I'm wondering if there's some limitation on the number of files on the root or somesuch, although 170 seems to be an unlikely limit - I seem to remember FAT16 can have like 512 entries in the root folder.)

---

### Post by dstew on 2008-02-29
> each block is therefore 128*1024*1024/65536 =2048 bytes. Which pretty much blows my original idea out of the water.Actually, it depends on how many files are on the drive. If the block size is 2048, then on average each file will waste 1024 bytes. If you have 10,000 files, there goes 10 Mb...Of course the files would have to be really small.

---

### Post by .nedberg on 2008-02-29
I am copying the files to the root of the drive. As I said the operation stops at 170 files. There are no more files on the drive.

I just tried to see if copying into a folder would change things, and it did! I made one folder and copied the files into that folder. Operation finished with no problem. Must have hit that root file number limit!

Thanks for your help!

---

### Post by ByteJuggler on 2008-02-29
> **.nedberg said:**
> I am copying the files to the root of the drive. As I said the operation stops at 170 files. There are no more files on the drive.

I just tried to see if copying into a folder would change things, and it did! I made one folder and copied the files into that folder. Operation finished with no problem. Must have hit that root file number limit!

Thanks for your help!

Odd, well I'm glad you got it sorted! :-)

---

### Post by jeffus_il on 2008-02-29
Great, it must be a fat 16 limitation, wonder if fat 32 will give more directory entries?

---

