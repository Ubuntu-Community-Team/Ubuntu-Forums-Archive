---
title: "Copying DVD to hd takes looong.."
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by anaconda on 2006-06-20
I am copying DVD:s to my hard-disk. One 4GB DVD takes about 28min to copy!! 
Shouldn't it go faster?
Why is it so sloooooooow?

DMA is enabled on the dvd-drive. Don't know about hd, but it is new and fast sata hd. Does it need DMA enabled too?

---

### Post by linuchsan on 2006-06-20
you can test the speed for your sata drive with hdparm -Tt /dev/sda

---

### Post by anaconda on 2006-06-20
> 
root@ubu:/home/ubu# hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads:   1752 MB in  2.00 seconds = 874.82 MB/sec
 Timing buffered disk reads:  174 MB in  3.01 seconds =  57.89 MB/sec

root@ubu:/home/ubu# hdparm /dev/sda
/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9729/255/63, sectors = 156301488, start = 0


is that slow?
I also copied the output of hdparm /dev/sda, and there isn't any mention of DMA..should there be, or is it just CD/DVD thing?

I also noticed, that the whole computer slows down when copying.. even the mouse moves slowly, and not smoothly.

---

### Post by NeghVar on 2006-06-20
Copying a dvd, expecially an encoded DVD movie takes a lot of resources

---

