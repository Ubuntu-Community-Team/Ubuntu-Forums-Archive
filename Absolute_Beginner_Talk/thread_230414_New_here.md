---
title: "New here"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by neogeo on 2006-08-05
[COLOR="Blue"][SIZE="5"]Hi All
New here. Just got Drake installed about 1am this morning
Got sound. Haven't checked printer or anything else yet. Hopefully all will go well
A friend is installing Drake as we speak in Korea and my son should be installing it sometime soon.

[/SIZE][/COLOR]

---

### Post by Jagot on 2006-08-05
Welcome to the forums.  Just don't use that size font all the time though :)

---

### Post by neogeo on 2006-08-06
ok

---

### Post by ubuntu27 on 2006-08-06
> **neogeo said:**
> [COLOR="Blue"]Hi All
New here. Just got Drake installed about 1am this morning
Got sound. Haven't checked printer or anything else yet. Hopefully all will go well
A friend is installing Drake as we speak in Korea and my son should be installing it sometime soon.

[/COLOR]

Welcome to the Ubuntu Community NeoGeo :)

So far, how's your experience with Ubuntu GNU/Linux? :idea:  :D 



I think this thread should be under "Ubuntu Cafe"

---

### Post by neogeo on 2006-08-06
What is ubuntu cafe?
I'm really impressed with 6.06 so far.
Seems to have found all my hardware- printer -logitec webcam - SB Live -nvidia card it's a 4800. 
Have a question about the nvidia card. I was poking around in the system info
(most of which is complete gibberish to me right now) and noticed a line;
something like srl driver 4163. Has ubuntu loaded a 41.63 nvidia driver for linux on install rather than just some generic driver to get the video up and  and running that does not take a advantage of all the cards features

---

### Post by ubuntu27 on 2006-08-08
> **neogeo said:**
> What is ubuntu cafe?
I'm really impressed with 6.06 so far.
Seems to have found all my hardware- printer -logitec webcam - SB Live -nvidia card it's a 4800. 
Have a question about the nvidia card. I was poking around in the system info
(most of which is complete gibberish to me right now) and noticed a line;
something like srl driver 4163. Has ubuntu loaded a 41.63 nvidia driver for linux on install rather than just some generic driver to get the video up and  and running that does not take a advantage of all the cards features

Here is a guide for installing nVidia drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

And about the [Ubuntu Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11")

It's a forums for general discussion, a community chat. Since you were not asking for help in this thread I thought that place is suited.

If you love ubuntu, and want to share your experience, visit:
[URL="http://ubuntuforums.org/forumdisplay.php?f=103"] :KS 
Check out "Ubuntu Testimonials"[/URL]


Happy "ubuntuing"

---

### Post by neogeo on 2006-08-08
Thanx 27
Have been poking around on the site and it looks like I need to read the Ubuntu Book first, make some notes and use the Wiki
Then just noodle around on the desktop and command line until I'm comfortable. Then sort out all my hardware.

It's like having a brand new computer.

I learned some BASIC on a TI 99a back in the 80's; my youngest brother was president of the users club here in town for several years.
Then I made a point of staying away from computers (to many late late nights)until the 90's; When
I got an old 486 with no install disc and ended up running DOS 6 so I'm familiar with the command line.
Around 2000 I bought a 566 celeron and got into racing Motocross Madness 2 online a bit and overclocking. The celery ran for several years at 969 Mhz aircoolled.

Have build a couple of computers since then running pirated XP until recently when I needed a new hard drive and bought a legal copy it was getting to be a hassle getting updates. So anyway I understand the the hardware a bit.
Since I own a copy of XP I plan on dual booting but I can see already that I will be spending a LOT less time in XP and a LOT more time in Ubuntu.

My friend in Korea has installed Ubuntu on a P3 Samsung laptop (not available in N.A.) but has not got it on the net yet.
I'm sure he will get it online sooner or later. 

One question is there backup program for Ubuntu like Drive Image or Norton Ghost that will work with a USB 2 external Hard drive?

---

### Post by ubuntu27 on 2006-08-09
The [Official Ubuntu Book]("http://www.phptr.com/bookstore/product.asp?isbn=0132435942&rl=1") looks great, I think I will buy that one too :)



Backups can be done using the Terminal, try to look for some guide or "How-tos" for backup.



Here is some apps:

["sbackup" ]("http://packages.ubuntu.com/dapper/admin/sbackup")

> Simple Backup Suite is a set of backend backup daemon and Gnome GUI frontends that provide a simple yet powerful backup solution for common desktop users.

Backups can be written to local directory or remote servers using Gnome VFS technology. A fine control is possible regarding what folders and files to backup. Files can be excluded even with a set of regular expressions. Regular backups can be scheduled.

This tool has been written with Google sponsorship during Summer of Code 2005 with mentoring help from Ubuntu. 


["mondo"]("http://www.mondorescue.org/") 

> Mondo is reliable. It backs up your Debian GNU/Linux server or workstation to tape, CD-R, CD-RW, NFS or hard disk partition. In the event of catastrophic data loss, you will be able to restore all of your data [or as much as you want], from bare metal if necessary. Mondo is in use by numerous blue-chip enterprises and large organizations, dozens of smaller companies, and tens of thousands of users.

Mondo is comprehensive. Mondo supports LVM, RAID, ext2, ext3, JFS, XFS, ReiserFS, VFAT, and can support additional file systems easily. It supports adjustments in disk geometry, including migration from non-RAID to RAID. Mondo runs on all major Linux distributions and is getting better all the time. You may even use it to backup non-Linux partitions, such as NTFS. 

["partimage"]("http://packages.ubuntu.com/dapper/admin/partimage")

> Partition Image is a partition imaging utility: it saves partitions in the Ext2FS (the linux standard), ReiserFS (a new journaled and powerful file system), NTFS (Windows NT File System) or FAT16/32 (DOS & Windows file systems) file system formats to an image file. Only used blocks are copied. The image file can be compressed in the GZIP/BZIP2 formats to save disk space, and split into multiple files to be copied onto removable media (ZIP for example), burned on a CD-R, etc.

This makes it possible to save a full Linux/Windows system with a single operation. In case of a problem (virus, crash, error, etc.), you just have to restore, and after several minutes, your entire system is restored (boot, files, etc.), and fully working.

This is very useful when installing the same software on many machines: just install one of them, create an image, and just restore the image on all other machines. Then, after the first one, each installation is automatic made, and requires only a few minutes. 

[Ubuntu's package Search Engine]("http://packages.ubuntu.com/")

---

### Post by Roasted on 2006-08-09
You say Linux found your printer easily. What kind of printer do you have? I have an Epson CX4800 and I have YET to get Linux to recognize it. :mad:

---

### Post by ubuntu27 on 2006-08-09
Re-reading your post, I noticed that you asked whatever there is a program for backing up in a EXTERNAL USB HARD DRIVE.

I'n not really sure but, a external HD should be able to use without any program. Just access and save stuff it like any other HD. 

I have a external USB DVD-burner and it works flawlessly. From the moment that I connect the DVD-burner, Ubuntu recognized it and displayed an icon in "Places" 
All I had to do was drag and drop or copy and paste my files to the  DVD-rw drive using nautilus (compare windows explorer) and click on "burn"

I've heard that a external device that used USB have more chance of being supported in GNU/Linux than others. So far I only own a Digital Camera (uses USB) and the DVD-burner that I mentioned above, but of which works without any problem.

So, your External HD should work, I believe.



And your friend in korea... I hope he is dual booting so he can get help online in the forum or IRC. [-o<  So far networking in Laptops seems to be a pain (I don't own a Laptop). 


Good luck! :KS

---

### Post by neogeo on 2006-08-09
Oh no another 400 page computer book!!!
I thought it was all online or in the examples folder...
But I will probably get a copy eventually. Looks like an excellent reference.
It looks like the chapters on the install cd will keep me going for a fair while.
Thanx for the links 27 looks like partimage will do the trick.

Roaster my printer is a Canon BJC 2100 about 5yrs old. Amazed it still works really.
My bud in Korea has a year old HP and it works to.

---

### Post by ubuntu27 on 2006-08-09
> **neogeo said:**
> Oh no another 400 page computer book!!!
I thought it was all online or in the examples folder...
But I will probably get a copy eventually. Looks like an excellent reference.
It looks like the chapters on the install cd will keep me going for a fair while.
Thanx for the links 27 looks like partimage will do the trick.

Roaster my printer is a Canon BJC 2100 about 5yrs old. Amazed it still works really.
My bud in Korea has a year old HP and it works to.

Yeah, everything you find in [that book]("http://www.phptr.com/bookstore/product.asp?isbn=0132435942&rl=1") can be found online, like in the [Ubuntu Forums]("http://ubuntuforums.org/index.php"), [Wiki]("http://wiki.ubuntu.com/"), and other Linux web site.
But, who knows that someday you ( or me) will not be able to accesses the Internet? 
That's where the physical book comes to the rescue ;)

---

