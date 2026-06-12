---
title: "Removed XP, Move / ?"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by rasfos on 2007-11-30
I was dual booting with XP but I made the switch completely to Ubuntu.  Because I was dual booting my root partition is at the end of the hard drive.  From what I understand, my system would be considerably faster if it was at the beginning of the drive.  Is this correct?  Is it possible to move the partition or would I have to reinstall?  I am assuming that I should also move my swap partition?  I have tried using Gparted but it doesn't look like it will do what I need.  Any help would be greatly appreciated.  Thanks.

---

### Post by skymera on 2007-11-30
i cant see why it would make a difference. mines at the end.

---

### Post by Sef on 2007-11-30
Some operating systems need to be on the first partition (Windows, FreeBSD), but GNU/Linux does not.

---

### Post by david_2001 on 2007-11-30
I don't think that either Gparted or Partition Magic can move the likes of an ext2/ext3 partition.  I'd just leave everything where it is, use the old XP partition as extra data space and reformat/reinstall at leisure.

---

### Post by jordanmthomas on 2007-11-30
> **skymera said:**
> i cant see why it would make a difference. mines at the end.
He may think this because if the data is closer to the start of the disk (towards the inside of the circle) the disk won't have to wait as many revolutions until what it wants comes around compared to the outside of the circle..

I don't believe this really makes a difference (or is even accurate), but it could be where his thinking is coming from.

---

### Post by rasfos on 2007-11-30
> **jordanmthomas said:**
> He may think this because if the data is closer to the start of the disk (towards the inside of the circle) the disk won't have to wait as many revolutions until what it wants comes around compared to the outside of the circle..
.

This is what I had read.  I read that the outside or end of the disk was from 2 to 3x slower than the beginning and since the OS is on the end of the disk, it would perform better at the other end.  I do not have performance problems but if I could speed up the OS by 2 to 3x then it would be worth the adjustment.  If this is not the case then I will leave it the way it is.  All, thanks for your very speedy responses!!!  :)

---

### Post by irish_flu on 2007-11-30
> **rasfos said:**
> This is what I had read.  I read that the outside or end of the disk was from 2 to 3x slower than the beginning and since the OS is on the end of the disk, it would perform better at the other end.  I do not have performance problems but if I could speed up the OS by 2 to 3x then it would be worth the adjustment.  If this is not the case then I will leave it the way it is.  All, thanks for your very speedy responses!!!  :)

Nah, I don't think you see a difference.  I suppose that technically the disk would have less area to seek when it fired up the reading head, but that time would be measured in milliseconds (or less).

---

### Post by jordanmthomas on 2007-11-30
That head moves so fast no human could tell a difference:
[http://www.metacafe.com/watch/318610/inside_a_hard_drive_see_what_goes_on_inside/](http://www.metacafe.com/watch/318610/inside_a_hard_drive_see_what_goes_on_inside/)

---

### Post by jordanmthomas on 2007-11-30
> **Sef said:**
> Some operating systems need to be on the first partition (Windows, FreeBSD), but GNU/Linux does not.

I've installed both Windows and FreeBSD on a partition other than the first.  Did I just get lucky or somehow beat the system?  :popcorn:

---

