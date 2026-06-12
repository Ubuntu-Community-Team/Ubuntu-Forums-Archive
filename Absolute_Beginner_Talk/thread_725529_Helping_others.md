---
title: "Helping others"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by &#54620;&#55148;&#47581; on 2008-03-15
Hey Folks,

I know it's been a while since I've posted here because I haven't had the hardware to make my new box (giving the old one to someone else) but now it will be arriving sometime next week.

I unfortunately cannot go for a fully ubuntu-only install, Adobe hasn't released the creative suite for Linux yet :(

I will be partitioning the new drive as follows:

1. NTFS 32-Bit Windows XP Partition. Contains all programs related to XP, but other than installed programs all other files will go to #3.

2. ???? Filesystem 32-bit Ubuntu (For now I'll avoid 64). I'm not sure what filesystem should be used for an ubuntu install, since my experience with it has always been with wubi on an NTFS drive. If Virtualbox (or another alternative) to run XP through a virtualization environment or compatibility layer (a la WINE) for all of my work needs then I think I may need to make another partition. 

3. NTFS Storage Partition. Here all non-installation files (Music, Photography, PSDs, Websites, Projects, etc) reside. I'm hoping due to it being NTFS that Windows XP as well as Ubuntu will be able to access and use the drive without issue. I believe this is correct but please let me know if I am mistaken. 

I think there's only one piece of hardware that may give me issues (Linksys WUSB300N USB Wireless-N Adapter) but I believe I still have the thread that solved this issue saved somewhere. Just in case though, I will list out the hardware of my new box:

Motherboard: MSI K9A2 Platinum AM2+/AM2 AMD 790FX ATX AMD Motherboard

Video Card[s]: DIAMOND Radeon HD 3870 512MB 256-bit GDDR4 PCI Express 2.0 x16 

CPU: AMD Phenom 9600 Agena 2.3GHz Socket AM2+ 95W Quad-Core Processor Model 

Hard Drive[s]: Western Digital Caviar 500GB 7200 RPM SATA 3.0Gb/s 

Sound Card: Creative X-Fi series

Optical Drive: Generic Samsung DVD +/- RW

Memory: OCZ 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit

External: 
Keyboard and mouse are generic Dell USB Keyboard and mouse.
Linksys Wireless-N USB Adapter
Wacom Tablet & Stylus

As I will have this box assembled soon (my first time building from scratch! woo~) I would like to start learning a little more about the operating system for example like learning my way around the command line would be nice. I'm just not sure what source I should use. There seem to be a lot of guides for linux in general, I'm just not sure which one to go with. I also have a copy of Linux for Dummies (Publication date: 2005) which I thought I might be able to read a little bit into if you guys don't think it's too outdated to not be valid for use in ubuntu (I'm not sure how much linux has changed since then) Whats your advice?

I hope to learn even just a little so that I can help address problems that others may have at the starting gate, eventually helping with more complex issues. 

Hoo, that was a lot longer than I intended! Sorry :(

---

### Post by forrestcupp on 2008-03-15
how do you pronounce your forum user name?

---

### Post by hhhhhx on 2008-03-15
> **forrestcupp said:**
> how do you pronounce your forum user name?
+1

---

### Post by Mogurijin on 2008-03-15
If you only need Windows for Photoshop, this might interest you:

[http://ubuntuforums.org/showthread.php?t=433359]("http://ubuntuforums.org/showthread.php?t=433359")

As for a file system, your probably fine with ext3 (the default).

---

### Post by Dr Small on 2008-03-15
> **xhhux said:**
> +1
+2

---

### Post by Joeb454 on 2008-03-15
I'll bring the total to +4 (I think) :lolflag:

---

### Post by &#54620;&#55148;&#47581; on 2008-03-15
> **forrestcupp said:**
> how do you pronounce your forum user name?

Hahaha, you just made my day. It's pronounced "hanhuimang" 

&#54620; "Han" like hah with an n at the end. &#54620; in this case means One (can't put spaces in usernames)
"hui" like putting an H before Wee
"Mang" Like Mah + ng

&#54620; &#55148;&#47581; = One Hope.

[QUOTE=Mogurijin]  	
If you only need Windows for Photoshop, this might interest you:

[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

As for a file system, your probably fine with ext3 (the default). [/quote]

(Not sure if this matters much) I use all programs from the CS3 Design Premium Pack (Photoshop, InDesign, Dreamweaver, Flash, Illustrator, Acrobat).

I actually have that thread bookmarked but I thought someone said in it that Virtualbox stopped working in Gutsy. I'll look through it again and see if anything has changed. Thanks for the reminder! 

I do use my computer for gaming as well, but that is why I will have an XP partition for anything that doesn't run decently under WINE or virtualbox, which actually is a little convenient because it separates work and play to an extent.

---

### Post by jken146 on 2008-03-15
A couple of pointers about partitioning:

Put the Windows partition at the start of the disk, and install Windows first.

You won't need more than 10 GB for your Ubuntu root (/) partition.  The format should be ext3.

The shared storage partition can be NTFS, but do not try to make this your /home -- NTFS does not support file permissions, so you wouldn't be able to log in!  In the Ubuntu installer, use the manual option and choose something like /media/storage as the mount point.  By the way, you could make it ext3 and use the Windows drivers at [http://fs-driver.org](http://fs-driver.org).

You'll want a swap partition (Linux virtual memory), not more than 1 GB in size.

---

### Post by Sef on 2008-03-15
> I'm not sure what filesystem should be used for an ubuntu install, since my experience with it has always been with wubi on an NTFS drive.

Use the default file system- ext3.

> NTFS Storage Partition. Here all non-installation files (Music, Photography, PSDs, Websites, Projects, etc) reside. I'm hoping due to it being NTFS that Windows XP as well as Ubuntu will be able to access and use the drive without issue. I believe this is correct but please let me know if I am mistaken.

To write to NTFS, you will need to download NTFS Configuration Tool (aka nfs-3g), which is available in the repositories.

---

### Post by bollix47 on 2008-03-15
You may also want to consider creating a separate partition for /home.

This will allow you to reinstall Ubuntu, should the need arise, without overwriting the data and configuration files that you have created.

---

### Post by JoshuaRL on 2008-03-15
Other problems you might have:

1).  Video card.  ATI is notorious in linux for not being well supported, although it is and has gotten better.  For someone new, I would suggest [Envy.](http://www.albertomilone.com/nvidia_scripts1.html)  It makes it easy to install the ATI drivers.  Just remember that when upgrade time comes, you'll need to uninstall Envy first.

2).  Storage Partition.  You can either use NTFS or ext3, and download the bits on the other OS.  But I would suggest using ext3 as the storage partition, since its just overall better.  For instance, with ext3 you won't need to defrag for years.

3).  Learning Ubuntu.  Yes, a lot has changed since 2005.  First, remember this site and the [Canonical](https://help.ubuntu.com/) and [Community](https://help.ubuntu.com/community/) help sites for any problems you may encounter.  For learning, try [Linux Command](http://www.linuxcommand.org/) for help in the terminal (very powerful and useful knowledge), [the Ubuntu Guide,](http://ubuntuguide.org/wiki/Ubuntu:Gutsy) and [Free Ubuntu eBooks.](http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html)

Lastly, I would like to commend your attitude.  That feeling of wanting to learn and then pass on the knowledge to others in need is what makes Open Source great.  Welcome to Ubuntu.

---

### Post by &#54620;&#55148;&#47581; on 2008-03-16
> **JoshuaRL said:**
> Other problems you might have:

1).  Video card.  ATI is notorious in linux for not being well supported, although it is and has gotten better.  For someone new, I would suggest [Envy.](http://www.albertomilone.com/nvidia_scripts1.html)  It makes it easy to install the ATI drivers.  Just remember that when upgrade time comes, you'll need to uninstall Envy first.


Well since most of the significant use of the video card will be done in Windows (gaming, etc) I'm not too worried about it as long as the drivers don't set the fan speed to 100% (Please tell me they don't :( ) 

> **JoshuaRL said:**
> 
2).  Storage Partition.  You can either use NTFS or ext3, and download the bits on the other OS.  But I would suggest using ext3 as the storage partition, since its just overall better.  For instance, with ext3 you won't need to defrag for years.
I was wondering if Defragging an NTFS partition would cause problems when reading/writing to it on Ubuntu, but hey ext3 is fine as long as I can read & write from it on either OS.
Edit: or if Defragging an Ext3 on Ubuntu would cause problem when reading/writing to it on Windows XP

> **JoshuaRL said:**
> 
3).  Learning Ubuntu.  Yes, a lot has changed since 2005.  First, remember this site and the [Canonical](https://help.ubuntu.com/) and [Community](https://help.ubuntu.com/community/) help sites for any problems you may encounter.  For learning, try [Linux Command](http://www.linuxcommand.org/) for help in the terminal (very powerful and useful knowledge), [the Ubuntu Guide,](http://ubuntuguide.org/wiki/Ubuntu:Gutsy) and [Free Ubuntu eBooks.](http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html)
Alright, I'll start into some of those to get a better feel for the operating system, thanks! 

> **JoshuaRL said:**
> 
Lastly, I would like to commend your attitude.  That feeling of wanting to learn and then pass on the knowledge to others in need is what makes Open Source great.  Welcome to Ubuntu.

Thank you, that's very sweet of you to say that. I've received a lot of help in the past for computer-related things that taught me a lot about how things work, but I haven't had the chance to really pay it back (save for preventing my father from setting the house on fire) so I feel obligated to show my appreciation by helping others :)

---

### Post by MVW01 on 2008-03-17
Hello there! Having been a programmer for years and sometimes on unix etc - I have just tried ubuntu for the first time on a platform that did not have a legal windows!  I must say this is a fantastic OS, simple to install and understand. The way this is going it could make it into the house because 'finally' I think my wife and the ordinary person could use it without needing a geek PHD!
   HELP!!! But hang on!  I cannot see how to install Acrobat reader of Flash player or equivalent so am a bit stuck surfing and using Firefox.
  Can anyone point me int he right direction please???
Michael <><

---

### Post by Perfect Storm on 2008-03-17
> **MVW01 said:**
> Hello there! Having been a programmer for years and sometimes on unix etc - I have just tried ubuntu for the first time on a platform that did not have a legal windows!  I must say this is a fantastic OS, simple to install and understand. The way this is going it could make it into the house because 'finally' I think my wife and the ordinary person could use it without needing a geek PHD!
   HELP!!! But hang on!  I cannot see how to install Acrobat reader of Flash player or equivalent so am a bit stuck surfing and using Firefox.
  Can anyone point me int he right direction please???
Michael <><

Are you using 32-bit or 64-bit?

First you need to enable some stuff in the "sourcelist". You can do that by Systems tab ---> Administration ---> Software sources

In this application you can enable alot of sources which allow you to easely install more stuff (:guitar:)
When done close it.

Next you have to enable  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

When done. you can find both Adobe and flash in synaptic Package Manager

---

