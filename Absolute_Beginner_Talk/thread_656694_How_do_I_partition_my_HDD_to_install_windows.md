---
title: "How do I partition my HDD to install windows??"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-01-02
So right now I am running Ubuntu off my Ex HDD (I have no internal hdd.) My biggest problem is that I don't know how to unmount the drive for partitioning. I was told to try the live cd ,but even then the partition is still "locked."

Also if I can get that solved, I still have no dual boot experience so I do not know how this will work. How do I choose which partition I want to boot at startup? If anyone can guide me here that be awesome. Thanks for your time and patience.



ps. Why do I have this this "extended" partition?" Can I remove it? 

[http://img211.imageshack.us/img211/1054/screenshotpk3.png](http://img211.imageshack.us/img211/1054/screenshotpk3.png)

---

### Post by 449 on 2008-01-02
Should I post this in a different thread?

---

### Post by jken146 on 2008-01-02
Don't worry about Extended -- it's just a way to get more partitions on one disk than are normally allowed.  The only "real" partitions are / and swap.

If you want to completely remove ubuntu and everything on your hard drive and then install windows on it, just boot up with a windows install CD and delete all the partitions in the Windows installer.

Otherwise, use a live CD.  Right-click on partitions in gparted to unmount them.

---

### Post by jpittack on 2008-01-02
The live cd you can use is gparted.  Get it from their website.  Extended partitions are primary partitions that can have logical partitions inside of them.  Don't worry about it.  I would suggest having atleast one anyways.

---

### Post by chronic on 2008-01-02
dont remove the exstended partition

but to install windows on top on linux you will have to do a fw things 

the first is resizing the partition you have no free space so you will have make you main linux partition smaller this isnt hard simply boot up the live cd  click, it might be called hda or something similer (sda) (1,2,3 blah blah) and click the unmount button

then open partion editer and resize it to allow room for windows ( leave linux swap alone)

the problem you will them have in windows itself since windows isnt compatable with linux you will have to reinstall grub (im sure youlll find plenty of posts on doing this)

---

### Post by 449 on 2008-01-02
> **jken146 said:**
> Don't worry about Extended -- it's just a way to get more partitions on one disk than are normally allowed.  The only "real" partitions are / and swap.

If you want to completely remove ubuntu and everything on your hard drive and then install windows on it, just boot up with a windows install CD and delete all the partitions in the Windows installer.

Otherwise, use a live CD.  Right-click on partitions in gparted to unmount them.

Thanks for the response! 

I don't want to remove Unbuntu I want to create another partition then install windows on that so I can dual boot. But it's "locked" even when I use a live cd.

---

### Post by 449 on 2008-01-02
This dropped to the third page fast, basically if someone could answer my question that would be great!

---

### Post by Yoke &amp; Chung on 2008-01-02
Hi,

You cannot unmount it if you are booting from the hard disk, and hard disk has to be unmounted before you can create new partitions. Set your computer BIOS to boot from CD, and boot the LiveCD from there. You should be able to unmount the external hard disk this way.

The LiveCD comes with Gparted, you can find this under:
"System--> Administration --> Partion Editor"

You can re-partition your disk with the above. Good luck!

---

