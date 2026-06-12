---
title: "New to Linux -- Some Questions"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by NT4.0 on 2006-07-15
I've been trying for quite a time to switch to Linux and I learned the basics. However, I had constant problems with hardware -- FreeBSD refused to recognize most of my peripherals and Fedora Core didn't even get installed. Ubuntu is the first Linux system that recognized virtually everything -- even the scanner which is stated to be meant only for Windows and Mac! It connected to the Internet and read my USB flash drive without trouble. I really enjoy working with this system. Still I have some general questions about Linux as I've worked with Windows for more than ten years.

Can I have more than one Linux partition? In Windows, I have three: the primary "SYSTEM" NTFS partition, the one with Windows, and the extended partition with two "DATA" NTFS partitions, where I keep all my data. In this case, whatever happens to the operating system, even its reinstallation won't touch the data files. In Linux, I can't find the way to do that. Keeping my data files on a system partition seems insecure to me. And I am not yet familiar with the recovery options Linux provides.

While Linux offers many programs I've worked with on Windows, like Mozilla Firefox/Thunderbird, OpenOffice, GIMP, I have no idea what programs may be equivalent to other which are important to me, such as Proxomitron, Miranda IM, 7-zip, FineReader, UltraISO, VMware. Probably there are their Linux clones or similar programs but I need someone to guide me on that.

I can't login as root in Ubuntu. I know that the root account has the same password as the only registered user (i.e. me), but when I try to log in as root with this password, the system refuses. What's the matter?

---

### Post by adam.tropics on 2006-07-15
You can indeed have multiple partitions, and in fact I would always suggest putting /home on a seperate partition. That way, reinstallations if needed, don't have to affect your data or settings. It's a big topic and worth researching further.[A starting point]("http://www.psychocats.net/ubuntu/partitioning.html")

---

### Post by Kobalt on 2006-07-15
Hello,

you can create virtually as many partitions as you want. To do so, start your computer with a Live CD of Ubuntu. In the Apps menu, you should find a tool named GParted : it will help you create, resize, delete partitions very easily. 
For the equivalents of your apps I know you can find an answer searching this forum or in google, try to search a website for equivalent apps win/linux, I know it exists somewhere... I don't know this myself, I would have helped you otherwise :) 

Cheers !

---

### Post by Obor on 2006-07-15
As said already you can have a separate /home partition. 

You don't login as root in Ubuntu (as default). If you need root priviledges you have to use sudo (superuser do) command. You will find explanations as to why in the manual or [here]("https://help.ubuntu.com/community/RootSudo").

A good start for programs could be [SourceForge]("http://sourceforge.net/index.php")

---

### Post by raldz on 2006-07-15
For Application equivalents in Linux, try this:

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by [S|G] on 2006-07-15
I won't get into partitioning since it is a big topic, as adam pointed out, and he also provided a nice reading material. I believe that what you're looking is a separate /home partition.

Now, as for the programs, take a look at this topic:
[http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183)

I also suggest that you familiarize yourself with synaptic (ubuntu) or adept (kubuntu), which are the package managers. You can find a lot of the things you are looking for there. Just search for **keywords** instead of program names and you should find what you need.

For example:
**DONT SEARCH:** Miranda IM
[b]SEARCH: instant messenger

Sometimes you won't find exactly the same programs. Instead, you'll find equivalent ones that work similarly (for instant messaging you can use gaim (ubuntu) or kopete (kubuntu), which are installed by default).

---

### Post by wildseven on 2006-07-15
HI!! I'm new to Ubuntu too! I'm really not sure I can help, but i'm sure these guru's can. I just wanted to welcome you to the linux scene, esp Ubuntu ^^
 - hope you find everything you need ^^ -

---

### Post by NT4.0 on 2006-07-15
Thank you for your replies. Surprisingly, I got Miranda IM working on Ubuntu via Wine. Amazing. Although it crashes sometimes, it seems usable. Most other Windows programs, such as WordWeb, don't work though.

So how do I make a separate /home partition? I checked out the Ubuntu partition editor but I don't know how to tell it to mount /home always on the partition I specify. Is it possible to make two /home partitions, like /home and /home2?

---

### Post by adam.tropics on 2006-07-15
[Another]("http://www.psychocats.net/ubuntu/separatehome.html") one for you...! I am not sure of the benefit of 2 home partitions though, i'd stick with one.

---

### Post by NT4.0 on 2006-08-14
Thanks a lot. It seems that I am ready to switch to Linux as I have downloaded and installed most of the software I usually work with and I figured out the way Linux deals with disk partitions. And it's great that Firefox and OpenOffice which are my primary apps for work are supplied with the system. What's wrong with Thunderbird, by the way?

There are some more questions which appear as I get new software for my Ubuntu installation. I could not play WMA music and AVI movies. is there a universal media player in Linux which can play most of the widespread formats? I have three (or I guess so) media players (two came with the system, and I also downloaded XMMS) and none can play that. Another problem was with floppies, I can read them and write on them, but the Floppy Formatter refuses to DOS-format my floppies saying every time that it is damaged (all of them! It just can't be so) and I didn't try to Linux-format them as I won't be able to use them on a Windows machine. Additionally, I had some problems with incorrect rendering of Russian fonts when using Gaim natively and Miranda under Wine. I want my system to be English but I also need to work with Russian. I know what to do about it in Windows, but here I have no idea where to tweak.

The final detail is the screen resolution. The maximum color depth is 24-bit and my Windows desktop supports 32 bit with 85 Hz (1024x768). Does it mean I will have to look for a Linux driver for my ATI Radeon video card to get better resolution, or may this all be done more easily?

---

