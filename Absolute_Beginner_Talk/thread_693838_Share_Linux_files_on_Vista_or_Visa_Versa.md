---
title: "Share Linux files on Vista or Visa Versa"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Zork on 2008-02-11
I'm getting ready to make the plunge to Kubuntu. I have some experience with Sun Solaris but have a Windoze background.

I have a Toshiba M400 Laptop which I am going to dual boot - Vista and Kubuntu. What I am planning on using Kubuntu for is a Webserver with Apache, PHP5 and MySQL. (I will also install those apps in Vista as well).

I would appreciate suggestions on how to share files between Kubuntu and Vista. I will be editing the PHP files in both OS' and from what I have been reading, it's better to use a program like explore2fs or fx-driver.org to be able to have Vista access the Linux partition than use a Linux utility to access the Windows partition (corruption issues).

Another thought would be to create another partition on my hard drive and format using FAT. That way I could mount the drive and Linux or see it in Windows.

What are your suggestions on which way to go?

(I plan on using both Vista and Linux to view the PHP webpages :-)

Thanks!

---

### Post by LowSky on 2008-02-11
i prefer the FAT32 method of sharing files.. as both OS can read it, but if you need support for files bigger than 4GB then I would use NTFS as both can read that as well, but you'll need to format under Vista.

---

### Post by amvella on 2008-02-11
I would go with making a separate NTFS partition. Then mount it in linux so u can access the files in it. In Vista it will appear automatically in My Computer. Hope this helps.

---

### Post by Zork on 2008-02-11
Thank you both for the information. Now I guess the question is FAT32 or NTFS? Is there a big difference? I don't plan on having any large files (they are only php pages for the moment..

---

### Post by Freddy on 2008-02-11
I just use the ext3 filesystem on my 'transfer' drive and mount that as ext2 from Windows using [fs-driver]("http://www.fs-driver.org/index.html"). The newest version even works with Vista.

---

### Post by Ek0nomik on 2008-02-11
The fs-driver previously posted works quite well.  I use it on one of my machines.  I also have all three of my external hard drives formatted as FAT32 so I can read them natively in Linux and Windows.  The choice is up to you really.

The question probably is which one is safer?  Using the drivers I would presume is less safe than just formatting to FAT32.  But, like I said, I haven't had any problems.

---

### Post by Freddy on 2008-02-11
Yeah fs-driver should be less safe but I have never actually have a problem using it. I have had some problems using a fat32 formatted partition (my own lack of intelligence) I needed to store some files larger than 4gb and with fat32  that a no-go.

---

