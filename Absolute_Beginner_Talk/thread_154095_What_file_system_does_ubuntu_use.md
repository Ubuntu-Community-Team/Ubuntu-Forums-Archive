---
title: "What file system does ubuntu use?"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by Grahamb on 2006-04-02
Can i install without burning the disk ? using a Virtual Image mounter ?(Daemon tools)

What file system does ubuntu use? and can i put the swap on another drive ?

the download is at 97% done
cheers, graham

---

### Post by rfruth on 2006-04-02
Best to use the Ubuntu install CD & at 97 percent your almost there - As for the Linux file system here is one of the better articles Ive seen [http://www.freeos.com/articles/3102/]("http://www.freeos.com/articles/3102/")

---

### Post by catlett on 2006-04-02
Ubuntu uses Fat 32. You need to burn the ISO file to a cd and boot  your computer from the cd. I don't know if it matters which drive the swap is on but I would try to keep it on the same disc. The swap doesn't have to be very big. You can keep it as small as 256mb but 512 to 1gig would be better. As you probably know it works like window's swap file except where windows makes a file for it, Linux makes a partition for it. The only thing you have to be aware of is if your windows partition is NTFS. There are issues with Linux and NTFS. For the most part you can read files from NTFS but won't be able to write to them.  Search around a bit for more info in the WIKI before installing if windows is NTFS, because if you use the GRUB boot loader it will be written to your windows partition at the MBR. This is a preetty thorough non-wiki guide [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)  Good luck

---

### Post by Grahamb on 2006-04-02
I've got it downloaded now, but do i have to burn it ?

---

### Post by joft on 2006-04-02
[QUOTE=Grahamb]Can i install without burning the disk ?[/QUOTE]

Well, you will need some media to boot from (and execute the Installer) ... a disk is one. Generally there should also be the possibility to start the Installer from a USB Stick, Floppy, Network, ... but since we are in the beginner forum here, I think the disk (CD) is the best method for you.

[QUOTE=Grahamb]using a Virtual Image mounter ?(Daemon tools)[/QUOTE]

No. You need to (re)boot your PC with a valid installation media (your disk). 

[QUOTE=Grahamb]What file system does ubuntu use?[/QUOTE]

During the installtion process you can chose from a list of filesystems: ext3 (default), ext2, reiserfs, ...

[QUOTE=Grahamb]and can i put the swap on another drive ?[/QUOTE]

Yes. Therefore you need to tell the Installer the right things during installation.

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=Grahamb]Can i install without burning the disk ? using a Virtual Image mounter ?(Daemon tools)

What file system does ubuntu use? and can i put the swap on another drive ?

the download is at 97% done
cheers, graham[/QUOTE]
I'll answer what I can. You can choose from 5+ filesystems that you want Ubuntu to use. The default is ext3 and reisersfs (sp?) is another popular choice. Ext3 is more stable then reisers but reisers is slightly faste. I would recommend ext3 though, since it doesn't fragment as much as reisers. I used ext3 for 3 months and I only got 3 % fragmentation. 

You can also put the swap on another driver but it wouldn't do much better in terms of proformance. Just but it on the same drive as Ubuntu for ease of use.

---

### Post by Grahamb on 2006-04-02
whats the best program to burn with when using windows XP ?

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=Grahamb]whats the best program to burn with when using windows XP ?[/QUOTE]
I would have to say Nero. I think you can get a fully functional trial from download.com.

---

### Post by catlett on 2006-04-02
Windows XP doesn't have a default program to burn an iso image. You need a commercial program for that. Do you have Nero or Easy Media Creator 8? There are alot of programs those sre just 2 popular ones. The main thing is you need a program that makes a disc from the image (burn the image to disk, create a disc from anb image on your hard drive). You do not want to make a copy of the file. There is a difference. If you don'r have a program try C-Net Downloads. They may have a free program or you can get a trial version. Good luck.

---

### Post by Grahamb on 2006-04-02
i will try burning with Magic ISO

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=Grahamb]i will try burning with Magic ISO[/QUOTE]
ok, make sure to burn it at a slow speed ! Try 4x. It may be slow but you will appreciate it during install. If you burn it at a slow speed, the install will so by very quickly and you won't have any problems. Good luck :)

---

### Post by NeghVar on 2006-04-02
> ok, make sure to burn it at a slow speed ! Try 4x. 

I dont no aboot that, it is good advice but i do all mine at48-52 speed and all have worked fine (about 6 difrent distros)

---

### Post by Grahamb on 2006-04-02
What write speed should i go for then ?

i have :
x2
x4
x8
x10
x12
x16

---

### Post by precinto on 2006-04-02
Alcohol 120% is a very good image manager and it also makes copys of your cd/dvds. I reccomend it. You can download the demo, i think it works for 30 days or so...

---

### Post by Kimm on 2006-04-02
[QUOTE=catlett]Ubuntu uses Fat 32[/QUOTE]

Not true! Ubuntu uses ext3 as default! it can read and write Fat 32 though...

---

### Post by Zeroangel on 2006-04-02
[quote=Kimm]Not true! Ubuntu uses ext3 as default! it can read and write Fat 32 though...[/quote]
And there is a utility for Windows to read/write to Ext2 and Ext3 drives, should you need it.

---

### Post by catlett on 2006-04-02
Because he appears to be new, I was assuming he wanted to know what to format his hard drive to. Most window people will know Ntfs, Fat32 and Fat. I did not think he knew the finer points of Linux installs. If he knew all that he would not be asking if he could install from a daemon tool instead of burning an iso to disc. So I gave him simple advice. Format the partition to Fat32. The problem I encountered when I got into Linux is everyone assumes you have a computer degree and give complicated answers. He is trying for the first time to install a Linux os. He probably heard about NTFS being a problem. So he posts about what file system and can he boot after downloading without making a disc. To me that means he is new so KISS(keep it simple stupid). Use Fat32 and burn the ISO to a disc and boot from that, make sure you are burning an image and not copying a file. Showing off your knowledge to someone less knowledgeable doesn't help people. They need simple instructions until they get more comfortable.

---

### Post by Zeroangel on 2006-04-02
Do not tell me that my solution is inferior just because you're too lazy to look into it.

It's not complicated at all. 
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm]("http://uranus.it.swin.edu.au/%7Ejn/linux/ext2ifs.htm")

It will allow windows to see your linux install as another hard drive (and be able to read files from it). I found this utility highly useful when I used it. FAT32 is an ok file system, but it corrupts easier then the Ext3 filesystem that ubuntu uses.

---

### Post by Grahamb on 2006-04-02
Thanks for all the help guy's i burned the iso using Magic ISO at x4 speed and it worked a charm. 
It booted into it and i went as far as the partioning screen and then aborted the install  because i need to figure out the way i want to install it as i want to bual boot with windows, on a 60GB drive

---

### Post by localzuk on 2006-04-02
Do not use FAT32 as it is not a good filesystem to use with linux. Period.

Ext3 is the one to choose.

---

