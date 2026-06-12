---
title: "Would I bennefit from Ubuntu"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by louishr on 2008-03-13
I'm a graphic artist and illustrator by trade, also I'm a gamer, I'm currently using windows xp. Linux has always been interesting to me, open source is a great idea, and I just like the idea of breaking away from microsoft. What I want to know is would I benefit from Linux. I don't much about computers outside of Windows so I've heard Ubuntu is the most friendly. Overall I guess I'm just curious and thinking about dual booting possibly. I really can't give up adobe cs3 suite, it's essential for my job and I dont think linux can run it. All I do on my computer right now is web, email, dowloads, listen to music, play games (crysis cod4 bioshock ect.) and most importantly use photoshop and illustrator. So I'm thinking to myself if i did go through the trouble of installing Ubuntu for a dual boot would i really use it all that much?

---

### Post by Dr Small on 2008-03-13
That's like setting a bowl of ice-cream in front of yourself and asking me if you think you will eat it. I don't know you, so I have no idea if you will eat it or not.

Same thing applies with Ubuntu. I have no idea if you will use it or not, as I do not know your personality. The best way to find out, is to try it and see how you like it :)

---

### Post by mcsimon on 2008-03-13
Photoshop cs2 runs well under wine but as far as I know cs3 won't work as of now. I think for the games you like to play and for your work you really need to stick with windows. However, if you like to experiment you should definately set up a dual boot with ubuntu - I assure you you'll enjoy it. I'm sure you'll find yourself spending most of the time when your not working or gaming in Ubuntu ;)

---

### Post by Hendrixski on 2008-03-13
YES!

I do a lot of graphics stuff with the GIMP, it does a lot of what Photoshop does.  Also, for quick things like business diagrams I use Inkscape.  And to make layouts for brochures or other desktop publishing and whatnot, I use Scribus.   Now, I'm not a pro, I just use these to get stuff done quickly for business, and it looks sharp.

As for the games... more XP games work on Linux with Cedega than work on Vista.... and ... there's no bloat like there is in Vista.... but... you want to play games on consoles anyway, not on computers... the PC gaming market is going to disappear in 5 years.

BTW, drSmall... I'm one of those rare people who hate ice cream, so .. yeah, you never know if someone would use it or not.

---

### Post by seanc7 on 2008-03-13
What programs do you use in your graphics work?

What games do you play?

---

### Post by louishr on 2008-03-13
i had mentioned it in my first post, i use adobe photoshop and illustrator both cs3 version i also use dreamweaver cs3 to maintain my website. As far as games i play Call of Duty 4, Crysis, Bioshock mostly

---

### Post by louishr on 2008-03-13
Ok I think the best thing for me to do is just jump in and install dual boot. I've done some reading and i see that you should really partition your drive so that you have xp on one ubuntu on one and a seperate partition for files to be shared inbetween the two in a FAT32 style. But in my search I found this site [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) which shows some different ways of partitioning. It recommends using FS-Drive to make windows be able to use Ext3 Partitions that way you can just have /home partition to save you settings and share files without the limitations of FAT32 (no file permissions, lots of fragmentation, and a file size limit of 4 GB). Would you recommend using the FS-Drive method? Also the only partitioning I've ever done was when installing xp so even once Figure out which partitioning plan to use I have no idea how to actually make the partitions. I have a big harddrive 500Gb so space really isn't an issue.


Also a side problem, I've downloaded and burned Ubuntu 7.10 but the live cd won't work it has problems with my graphics card (nVidia 8800GTS) so it will only go into safe graphics mode so I can't really use the live cd which I imagine will complicate my installation process a good bit.

I know I'm asking a lot but any help would be much appreciated.

---

### Post by sandysandy on 2008-03-14
> **louishr said:**
> Ok I think the best thing for me to do is just jump in and install dual boot. I've done some reading and i see that you should really partition your drive so that you have xp on one ubuntu on one and a seperate partition for files to be shared inbetween the two in a FAT32 style. But in my search I found this site [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) which shows some different ways of partitioning. It recommends using FS-Drive to make windows be able to use Ext3 Partitions that way you can just have /home partition to save you settings and share files without the limitations of FAT32 (no file permissions, lots of fragmentation, and a file size limit of 4 GB). Would you recommend using the FS-Drive method? Also the only partitioning I've ever done was when installing xp so even once Figure out which partitioning plan to use I have no idea how to actually make the partitions. I have a big harddrive 500Gb so space really isn't an issue.


Also a side problem, I've downloaded and burned Ubuntu 7.10 but the live cd won't work it has problems with my graphics card (nVidia 8800GTS) so it will only go into safe graphics mode so I can't really use the live cd which I imagine will complicate my installation process a good bit.

I know I'm asking a lot but any help would be much appreciated.

 here are some other links to dual booting:-

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

with 7.10 ubuntu can both read and write to NTFS (Windows partition).

i hope u burned the live CD as iso image on CD and not as data CD. only then will it work.

if live Cd does not work, try alternate CD.

for partitioning u can use gparted live Cd ( available on net for downloading)

regards

---

### Post by louishr on 2008-03-14
yes I burned as an image using Nero, so since 7.10 can read write NTFS there is no need to partition anything other than a 50-50 split half for Ubuntu half for Windows xp, is that correct?

---

### Post by perce on 2008-03-14
In principle yes, but it's a better idea to split the Ubuntu part of the disk into three partitions: one for the operating systems and the applications, one for your personal files, and one called swap, which is useful if your computer has not enough RAM or if you want to hibernate. There is a partitioning howto here: 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
it's slightly outdated, but the basics haven't changed.

The reason why you may want to separate the OS from your file is that you can later reinstall it if you need (and you'll need sooner or later) without losing your data.

---

### Post by octopuskevin on 2008-03-14
I'd almost say just hang on till hardy is released. It will ship with wubi which will let you install ubuntu from within windows like any other windows program. Now while you will lack some basic features like suspend etc... it should feel just like the OS would if you had actually installed it.

you can reboot into linux or windows, and when you get bored of it you can remove through windows add-remove section, or if you've fallen in love with linux, you can actually do a proper dual boot knowing what to expect [and love :P]

It seems that you got a lot of attachments to windows, and while a good chunk of them can be covered fine either through wine or other open source alternatives, you will notice that some high-end resource intense games will probably not run [even through wine]

anyways, wait till Hardy's april release and play around before you commit yourself to something

p.s. your boot into safe graphics mode is probably because you need to install restricted [proprietary driver] ... if you go to system --> admin --> restricted you can see if they exist, however since I think you need to restart for the changes to be effective, you won't really be able to experience that off of the live c.d.

---

### Post by Zeroangel on 2008-03-14
Hi and welcome. You should know that CS2 and earlier will work on linux through the WINE program (the windows compatability layer), and with a few tweaks to some text files you can even integrate opening in photoshop through your context (right-click) menus. Photoshop compatability is a priority for people who are developing wine so I estimate that it will take a few months before CS3 compatibility is added in.

Most high-end games will also not work. I can get certain games like System Shock 2 and Battlezone 2 running through wine, and there are dozens of other games (like well-known RTS games) that will work through it, but they will not work flawlessly. And really new games are not expected to work at all since they rely on windows functionality that is not yet build into wine.

You should know that there is a lot to linux. While the Ubuntu developers have taken great pains to make it easy to use from the get-go, you will still need to learn how to use some command line skills (and learn how/where to edit certain configuration files) if you ever run into problems or want to really push the limits of the linux OS.

Also about those people hawking GIMP, most of them do not work with graphics in a professional capacity and have no idea on how difficult it is to adjust to it. Though I must admit you can put out some pretty decent graphics with it.

As far as partitioning goes, I typically allocate 15GB or 15% (whichever is larger) to the base linux install, 15GB or 15% to the windows install, and the remainder to a shared FAT32 partition (that is easily accessible from both linux and windows -- to put games and media on).

 When Ubuntu 8.04 (Hardy Heron) is released in April. I suggest you give it a try, as only this version (and later) will have wubi. Through wubi (as octopuskevin mentioned), you dont have to worry about that yet if you just want to do a 'test' install of ubuntu (as wubi only makes temporary, easily reversable, changes to your OS setup).

---

