---
title: "Corrupt USB Key"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by slambrick on 2008-02-18
Can anyone recommend a tool or method to recover a corrupt USB key. it had fat16. In windows it wants to reformat it. in Ubuntu it doesn't see the key.

---

### Post by PhoenixP3K on 2008-02-18
Do you need to recover data on the USB key?
If Windows can see it I would recommand to format it to FAT32...
I did come across defective USB memory keys that lost the data all the time, had to format it again and again, then it wouldn't reformat at all. You might have a lemon (very pessimist answer... sorry)

---

### Post by dcstar on 2008-02-19
> **PhoenixP3K said:**
> Do you need to recover data on the USB key?
If Windows can see it I would recommand to format it to FAT32...
I did come across defective USB memory keys that lost the data all the time, had to format it again and again, then it wouldn't reformat at all. You might have a lemon (very pessimist answer... sorry)

The "Flash" technology used on USB stick devices still has a finite quantity of write cycles, some people claim because ***they*** have never experienced any problems that there is no limit, others seem to know better from (bitter) experience.......

If the block containing the partition information has died, then it unlikely that much data can be recovered from the OP's drive.

---

### Post by erginemr on 2008-02-19
I have to agree with the above posts that your chances are quite low. I had a crappy USB pen drive once, which always let me down with corrupted files no matter how much I formatted it with several tools and several file systems.

You can still try installing Gnome Partition Editor:
```
sudo aptitude install gparted
```
and using it to reformat your USB drive to vfat(fat16), if Gparted can see the drive, that is.

---

### Post by slambrick on 2008-02-19
> **PhoenixP3K said:**
> Do you need to recover data on the USB key?
If Windows can see it I would recommand to format it to FAT32...
I did come across defective USB memory keys that lost the data all the time, had to format it again and again, then it wouldn't reformat at all. You might have a lemon (very pessimist answer... sorry)

Yes I do need the data. I can see the files using a windows based recovery tool but due to its shareware limitations cannot access the files or complete the repair. I am really after something that will do the same in open source.

---

### Post by slambrick on 2008-02-19
> **erginemr said:**
> I have to agree with the above posts that your chances are quite low. I had a crappy USB pen drive once, which always let me down with corrupted files no matter how much I formatted it with several tools and several file systems.

You can still try installing Gnome Partition Editor:
```
sudo aptitude install gparted
```
and using it to reformat your USB drive to vfat(fat16), if Gparted can see the drive, that is.

Thanks for that I already have gparted installed so looked there and found the device listed with an unallocated partition. Do you think it's possible to repartition and then recover the files?

---

### Post by erginemr on 2008-02-19
You are welcome **slambrick**. If you are after recovering the files inside, then you should definitely try to recover them before the formatting.

In this context, I will suggest you to try testdisk:
```
sudo aptitude install testdisk
```
that has been reported as testing and fixing the errors in hard drives by many Ubuntu users. I have only played with it so far, and did not used in case of a real problem. But it is still worth a try.

Just install it, run "testdisk" from a terminal, let it check your corresponding drive (sdc something) and let us see what it offers...

---

### Post by erginemr on 2008-02-19
Speaking of GParted, you can do a file system check and possibly some error fixing from GParted:

Unmount the drive from GParted by right clicking on it, then select "check". I don't think that it will do wonders on a drive that reports as "unallocated" but who knows, still worth a try.

---

