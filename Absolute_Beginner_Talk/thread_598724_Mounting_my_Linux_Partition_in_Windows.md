---
title: "Mounting my Linux Partition in Windows"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by jolt459 on 2007-10-31
Hi!

I am new to Ubuntu, and I really love it, It's nice, simple (for me at least), and so far I love it.

I have one question though, when I'm in Windows, how do I view my Linux partition? Is there a certain way I can mount it? Because I don't see it in My computer. I can see my Windows Drive in Linux, but when I'm in Windows I can't see my Linux drive.

Thanks to all that can help me. And I'm sorry if this has been documented, I searched but I didn't find anything about it.:roll:

---

### Post by scrooge_74 on 2007-10-31
Hi welcome aboard.

From Linux side you can read your partitions and if  ntfs-3g is installed and configure you can write to it.

[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+driver+install](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+driver+install)

As from Windows to Linux is a trickier thing, there is something you can install but I dont know the name for it some else will probably come along in a minute with the explanation.

EDIT:  I think is this what you need for Windows [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by LaRoza on 2007-10-31
I recommend using a different partition for sharing data. Although you can read the Linux partitions with a certain app, it is not secure, and you don't want Windows messing with Linux.

You can use GParted to make a large partition of a format, like FAT32, or NTFS, that Linux and Windows can use.

-EDIT I realise I didn't name the app, I don't recommend it

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

[http://techpatterns.com/forums/about686.html](http://techpatterns.com/forums/about686.html) -- You can make the storage partition ext2, and use this advice.

---

### Post by newlinux on 2007-10-31
If you must look at your ext3 partitions in windows you can use [http://fs-driver.org/](http://fs-driver.org/)  Works for ext2 and ext3, but don't know if it works with Vista.

---

### Post by jolt459 on 2007-10-31
I can just create another partition for shared data, for media and such. But what format should I create it in?

---

### Post by sjordan on 2007-10-31
Here is a program that allows you to mount your Linux drive (ext2 or ext3 FS) to a Windows drive letter.

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Once set up, you can change the drive letter of any Linux partition through control panel.

---

### Post by ddrichardson on 2007-10-31
If its just to access the odd file then try [this]("http://www.chrysocome.net/explore2fs").

---

### Post by newlinux on 2007-10-31
> **jolt459 said:**
> I can just create another partition for shared data, for media and such. But what format should I create it in?

If you want easy compatibility with both OSs FAT32 would be the choice. Be aware of the 4.0GB filesize limit, and it will need defraging from time to time...

---

### Post by ajgreeny on 2007-10-31
I agree with ddrichardson, for copying files across to windows use **explore2fs.**  I know it works faultlessly as I have been using it since I have used linux without problem.  It simply explores and copies across the files without being able to write to the linux partition, and seems completely safe and effective.

---

