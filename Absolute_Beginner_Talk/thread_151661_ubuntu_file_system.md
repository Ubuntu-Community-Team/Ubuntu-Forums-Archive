---
title: "ubuntu file system"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by bobanshirl on 2006-03-28
I have Windows xp pro on my pc with E:\ C:\ D:\ and H:\ Windows is installed on the E:\ drive.I used Partition Magic 8 to get these drives.The other drives are empty.Can I just install Ubuntu on one of the other drives say C:\ and what file system does Ubuntu use ie NTFS or Fat32.

---

### Post by bobanshirl on 2006-03-28
Quick reply please

---

### Post by wsanders on 2006-03-28
Linux actually uses ext3, not FAT32 or NTFS. It can read NTFS, but not write, and it can write/read to FAT 32. While installing Linux, you can select one of those partitions (though it won't show up as C:\, etc.) and format it as ext3. You also will need a swap partition; the partioner can automatically format one of your partitions for both the ext3 and the swap.

---

### Post by Mustard on 2006-03-28
Ubuntu can use ext2, ext3, or reiserfs as a file system.  It has support for reading and writing fat32, but doesnt use that as its 'native' filesystem.

You could use partition magic to actually remove the extra partitions or partition that you don't need and leave it as 'free space' on the drive.  Then when you use the installer, you can tell the installer to use that free space and it will create its own partition using the native file format for linux.  Or you can do it as described above.

---

### Post by maxx_730 on 2006-03-28
If you install Ubuntu use this: [http://www.fs-driver.org/](http://www.fs-driver.org/) to read you ubuntu partition in Windows.

---

### Post by bobanshirl on 2006-04-20
Hi there,Thanks for your reply,I have downloaded it but am not sure if I should install it before or after I install Ubuntu.Where abouts are you located

---

### Post by bobanshirl on 2006-04-20
Hi there Sorry I have been so long answering,I have done what you suggested and deleted D and H.I now have C and E.The last time I reinstalled Windows I put it on to E.That last reply you sent when you refer to using the installer do you mean when I insert the Ubuntu Install disc or the Partition Magic program.Sorry to seem confused but I am new at this and I would like to install Ubuntu  alongside my existing Win XP Pro without it going all pear shaped and having to reinstall Windows.Rthanks for your interest.Bob in Verwood Dorset

---

