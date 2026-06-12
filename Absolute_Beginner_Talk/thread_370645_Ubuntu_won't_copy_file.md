---
title: "Ubuntu won't copy file"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-02-26
I need to copy a 6 gigabyte file from my desktop to an external hard drive. I've tried using the file browser, but the program crashed every time I get to 4 gigabytes. I've also tried copying the file using the terminal, but the program "cp" crashes.

Please help.

---

### Post by chewearn on 2007-02-26
Your destination drive is formatted to FAT32, which cannot hold any file larger than 4GB.  Unfortunately, instead of stopping the copy gracefully, Natillus will crash in this situation.

---

### Post by Ek0nomik on 2007-02-26
I would suggest you split the file up if you can.  Is it an image file by any chance?

---

### Post by Shack_ on 2007-02-26
I tried reformatting the hard drive in NTFS (using Windows, I couldn't figure out how to do it in Ubuntu), it worked, but then Ubuntu said I didn't have enough access privileges to write to the drive. I tried using the terminal and the "sudo" command, but it said that it "cannot create regular file '/media/usbdisk/filname: Read-only file system". 

Yes, it is an image file, and how would I go about splitting it?

---

### Post by Maestro23 on 2007-02-26
> **Shack_ said:**
> I tried reformatting the hard drive in NTFS (using Windows, I couldn't figure out how to do it in Ubuntu), it worked, but then Ubuntu said I didn't have enough access privileges to write to the drive. I tried using the terminal and the "sudo" command, but it said that it "cannot create regular file '/media/usbdisk/filname: Read-only file system". 

Yes, it is an image file, and how would I go about splitting it?

If you want to read/write to that NTFS drive from Ubuntu, you might want to look at  [COLOR="Red"]ntfs-3g[/COLOR]: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by chewearn on 2007-02-26
By default, ubuntu cannot write to NTFS formatted drive.  You need something like NTFS-3G installed.  Or, format the drive to ext2, then install ext2fs on the Windows side.  There are some thread in this forum discussing this subject already; do a search.

On the other hand, to find out more how to split file:
```
man split
```

---

### Post by xdarkxanarchyx on 2007-02-27
I just want to add that you can also format it to ext3 and still use ext2fs in windoze and see your hard drive with all it's contents.

---

