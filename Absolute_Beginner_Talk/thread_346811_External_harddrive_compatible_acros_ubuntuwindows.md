---
title: "External harddrive compatible acros ubuntu/windows?"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-01-26
I am about to make the switch from windows to ubuntu. But I first want to setup a dual boot system so as to still have the choice before swithing fully to linux. I now want to buy an external hard drive so I can just put all my music/movies/pics on that and I only have the os's on my computer. 
If I just put all my files on the exernal hard drive from windows, can I then also access them when I boot ubuntu? Or do I need to format it in a different way for linux... (which would make this whole plan worthless..)?

---

### Post by Catsworth on 2007-01-26
Ok, I'm a n00b here myself so please don't go for this until you've had confirmation from someone else but.....

The way I understand it is that Ubuntu (and other *nix variants) can read/write to/from Fat32 file systems so.....as long as you ensure that the external drive is formatted as Fat32 you shouldn't have any problems.

I'm not sure if you would run into any trouble with file permissions or types, but I think it should work ok (well, I hope it should - I've already ordered a nice NAS box to do just this :) ).

---

### Post by Happy_Man on 2007-01-26
Well, if you want to use the external drive as a storage and storage only, you can always format it as FAT32, a format that both Ubuntu and windows can read and write to natively. If you're gonna install Ubuntu on that hard disk also, you can use the partitioner during install to install Ubuntu and have free space. See [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning) for more help.

---

### Post by kramer65 on 2007-01-26
I just want files on the external hard disk. I have my internal hard disk which I will partition into two partitions (linux and windows) and I want to have my external hard drive with my music etc which i will then format to fat32. So I can read and play the music/movies from that hard drive. But can I also change files, delete them, or add files from both windows and ubuntu?

---

### Post by taurus on 2007-01-26
Yes.  Keep one thing in mind that you cannot store files over 4GB on fat32.  However, you can read and write to ext2/ext3 fine in Windows with [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by kramer65 on 2007-01-26
so what is the advantage of making the external hard drive a fat32 then. Can't I make it ext3 better then? As I understand you can read and write (also bigger files) to ext3 from both linux and windows? What is the difference between ext3 and fat32 then?

---

### Post by taurus on 2007-01-26
Fat32 is crapped while ext3 is much more superior.  That's why I told you that you can actually read and write to ext2/ext3 in Windows with the driver from that link.  The choice is up to you.

---

### Post by kramer65 on 2007-01-26
Ok thanks a lot. This helps me a lot. I have one last question though..
Why is ext2/3 way more superiour than fat32? quicker? less crashes? Something else?

---

