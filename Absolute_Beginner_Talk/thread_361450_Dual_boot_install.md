---
title: "Dual boot install"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by opus_az on 2007-02-14
Hello...

For a new computer I'm building I'm considering a dual boot with Ubuntu and either WinXP or Vista.

I'm a newb to both Ubuntu and dual booting. Any suggestions for which loader to use, or the 'best' harddrive setup? 

TIA,
D.

---

### Post by oilchangeguy on 2007-02-14
are you using a single drive, or multi drive set up? on a single drive you'll need to install windows first, then run the live ubuntu cd (i suggest version 6.06) when the desk top loads, select the install icon. and follow the prompts to allow you to install it along side windows.

---

### Post by opus_az on 2007-02-14
> **oilchangeguy said:**
> are you using a single drive, or multi drive set up? 

Since I haven't built the computer yet I'm open to suggestions. I don't have a problem using two or even three hardrives (one for data?). Whatever would be 'best'.

---

### Post by dannyboy79 on 2007-02-14
i would definitely install windows first on your "first" hard drive (means that this drive is booted by bios) then install ubuntu and chose to install grub boot loader on the first hard drives mbr. what this will do is overwrite windows boot loader with grubs, next time you try to boot it will boot to linux without giving you a choice to go into windows BUT, that's when you simply open up the neccessary grub file and add an entry so that you can then boot into windows. here is a great guide for ya! [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

the guide uses dapper but everything is applicable if you're using edgy or fiesty I believe. good luck

p.s.  (there is a search function at the top of the forum that you can use. you would have found tons of threads on this subject. also, gogle is a great source of info)

---

### Post by oilchangeguy on 2007-02-14
if you use one or more drives is up to you. if you have a lot of data, maybe a multi drive set up. just make sure you format windows fat 32, so you can get to data on the windows side, while in ubuntu.

---

### Post by dannyboy79 on 2007-02-14
> **oilchangeguy said:**
> if you use one or more drives is up to you. if you have a lot of data, maybe a multi drive set up. just make sure you format windows fat 32, so you can get to data on the windows side, while in ubuntu.


just to make sure you understand what he is saying. In a dual boot system, Windows XP likes NTFS, Ubuntu like ext3 (can be XFS, reiserfs and many others, I am trying to keep it simple). So when you boot to windows, the hard drives that are formatted as ext3 will have data on them, they will ony be able to be read and write if you use a third party driver called FS-DRIVER that you have to install into windows. Now on the other end, while you are boooting to linux, you will be able to "read" from NTFS without any other drivers installed BUT you can install a driver or program called NTFS-3G so that you have write support also. Now it's important for you to investigate and make your own decision about how comfortable you are using 3rd party drivers to write data to the hard drives or psartitions that are not native to that OS. What he is saying, is that FAT32 is a filesystem that has had support for writing to and reading from while in BOTH OS's for a LONG TIME. BUT the downside is that if you're storing games or movies, FAT32 can only hold files under 4GB. NTFS-3G was just released under RC1 so it has been around for quite awhile now and many people swear by it but it's all about what data you're writing to that NTFS partition from linux and how important it is to you. good luck

here are the applicable links:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by opus_az on 2007-02-15
Thanks all! :KS

---

