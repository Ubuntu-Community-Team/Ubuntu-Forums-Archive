---
title: "Duel XP-Ubuntu on SATA laptop"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by tuqann on 2006-10-10
Hello everyone,

Been going through the forums for a while, couldn't find anything close to what I'm trying to do here. Problem is, This is my first time working with any linux before, most of the words used in threads confuse me (dapper, GRUB, things like that). I'd appreciate all kinds of help here:

My situation is the following; I have to install a linux on my laptop because I have a few courses that require it. Ubuntu was my professor's choice (which version I don't know yet, he's supplying the CD but for now let's assume it's the lastest out there). I have a pre-existing winXP, doesn't matter really, I was planning on formating for preformence issues to start with, but the problem is I HAVE to have a winXP on my laptop to be able to access my university's wireless internet.

So, I got one SATA drive on my laptop, 80gigs, and have to have the two systems. Any ideas where should I start?

---

### Post by Aberrix on 2006-10-10
just partition/resize the drive (windows) and install ubuntu as normal.

---

### Post by bulldog on 2006-10-10
Just decide which part windows gets and what Ubuntu.

Then install windows first on it's own partition,and leave the rest of the space unallocated.

Then boot the live cd or the alternate what ever you have,and install Ubuntu.

When coming to gparted let it use the unallocated space or partition it yourself by making a 10GB / [root] and a 1GB swap file and the rest of the space you make /home.

---

### Post by tuqann on 2006-10-10
Does the order of installation matter? How will it boot (is it like when you have two versions of windows, say 2000 and XP, installed)? IS there a prefered installation order?

---

### Post by dannyboy79 on 2006-10-10
> **tuqann said:**
> Does the order of installation matter? How will it boot (is it like when you have two versions of windows, say 2000 and XP, installed)? IS there a prefered installation order?


yes order matters, WINDOWS first because otherwise windows would overwrite your grub install which is what will allow you to dual boot. i hope you don't mind but why would you need winbloz to access a university wireless internet. ubuntu is very capable of accessing wireless access points or wireless routers or whatever. it'll depend what kind of wireless card you have which will determine how much you'll have to do to get it work. you could find out by trying out the live cd first and see if you can get wireless to work before you completely get rid of winbloz! good luck

---

### Post by tuqann on 2006-10-10
Thanks for the info, sounds easier than I had imagined.
this is what I was thinking, please feel free to correct or suggest if I got anything off:

15gigs for XP and it's programs
14gigs for Ubuntu, 1 for swap
25gigs I make ntfs, for games and winXP files strickly
25gigs I make FAT32, for my files.

---

### Post by ReaderRat on 2006-10-10
> **Aberrix said:**
> just partition/resize the drive (windows) and install ubuntu as normal.
When you re-install XP, you will have an option to create a partition of any size (up to 80 Gig) for Windoze. Just make the Win partition 40 Gigs and leave the rest (40 Gigs) for Ubuntu. Windoze will partition 40 Gigs, format it, and install XP on it. This leaves unallocated space (40 Gigs) for Ubuntu. When you load Ubuntu and instal it, choose the unallocated area for Ubuntu. The installer will then partition, format, and install Ubuntu on that that partition.

EDIT: Sorry about the simple explanation, I thought you were another newbie.

---

### Post by tuqann on 2006-10-10
You'll have to forgive my university's computer services department, it's a little retarded. CNS at my university allows us to use wireless only through a special security client called VPN, with specific student-certificants that are locked on the computer. If I as much as change my account's password I have to request CNS to reset my certificant so I can log-in again.

It's very stupid, but everything is beta here (wireless's been on for a year, in a country that only has 56k and shared pirated DSL service). My university's very paranoid about illegal-access. sigh, I can't wait to get my senior year over with...

Thanks for all the info, I can't wait to start using Ubuntu!

---

### Post by dannyboy79 on 2006-10-10
> **tuqann said:**
> Thanks for the info, sounds easier than I had imagined.
this is what I was thinking, please feel free to correct or suggest if I got anything off:

15gigs for XP and it's programs
14gigs for Ubuntu, 1 for swap
25gigs I make ntfs, for games and winXP files strickly
25gigs I make FAT32, for my files.

it's just my opinion but i wouldn't do the extra 25gb for a seperate NTFS partition, i would either take 13gb and add it to your windows installation and runs the games from there and add 12 to your fat32 partition to store the "winXP files strictly" files onto the fat32 partition. that's just me though.

---

### Post by tuqann on 2006-10-10
hmmm, i very well could be wrong, but I had problems with FAT32 and large files (dvd images) on my external. you know if that's true? larger than 2.5 gig files won't copy onto a FAT32 partition?

---

### Post by gn2 on 2006-10-10
For your circumstances, if your Laptop has a high enough specification, I would suggest installing VMWare Server in XP and install Ubuntu in a Virtual Hard Drive.

Dual booting on one hard drive is not without it's hazards.

---

### Post by man-man on 2006-10-10
> **ReaderRat said:**
> EDIT: Sorry about the simple explanation, I thought you were another newbie.
I'm just another newbie, can you give me a simple explanation to something :mrgreen: 

I'm looking for similar  information - in advance of building a computer in case theres stuff I need to change.

Basically I'm looking to get it set up so that I have Ubuntu and WinXP installed in their own partitions on one big hard drive (with minimal space occupied by Windows) Then a big partition in whatever the latest Linux format is for both OS's to read from (Am I right that Windows will work fine reading/writing with a Linux format disk? If not then a small partition in NTFS format for some Windows stuff as well)

Actually thinking about it, the NTFS partition is probably necessary for some Windows-based stuff I'll want to install

umm.. any helpful information and/or links will be gratefully listened to :)

---

### Post by mahy on 2006-10-10
> **man-man said:**
> Am I right that Windows will work fine reading/writing with a Linux format disk? If not then a small partition in NTFS format for some Windows stuff as well

No you're not. Windows can only access Linux partition using 3rd party utilities and i've never seen a write support. (There are various utils offering read support for ext2/3, reiserfs, but not xfs!) Linux can read ntfs natively, but write support is still in experimental stages and not available in Ubuntu (not without some heavy modifications).

I'm having it half-half, windows and Linux, but if you feel you need a partition both systems can access, use FAT32. The sizes are up to you to decide.

---

### Post by man-man on 2006-10-10
ahh, that complicates things.. oh well, i'll figure something out - maybe I'll get 2 smaller discs, one for each OS then come back and bug people again for help with that ;)

<edit> what kind of size partitions would i need to install WinXP and Ubuntu into? and what other partitions would I need to set up (and what sort of size would *they* need to be?

---

### Post by bulldog on 2006-10-10
> **man-man said:**
> ahh, that complicates things.. oh well, i'll figure something out - maybe I'll get 2 smaller discs, one for each OS then come back and bug people again for help with that ;)

<edit> what kind of size partitions would i need to install WinXP and Ubuntu into? and what other partitions would I need to set up (and what sort of size would *they* need to be?

That depends a little what you wanna do with it.

If you do most things with windows and just fool around with Ubuntu it should be different then using Ubuntu mainly and windows to fool around.

That decision is your's to make :D 

But Ubuntu,for a little experimenting,make a 8-10GB / [root] partition and a swap about 512MB - 1 GB depending on how much RAM you have installed.
Your /home you can make as big as you want depending on what you want to do.

Windows need a 5GB for the install of the OS and the rest is your choice,again depending what you want to do with it.

To exange data between windows and ubuntu,you can make a small partition of about 5GB FAT32,but if you want to exange many DVD's it should be bigger.

It's all depending what **you** want to do with it.:D

---

### Post by man-man on 2006-10-10
hehe, and therein is both the great thing about linux, and a slight problem for me (i'm bad at decision making ;) )

But all I needed in terms of information was the actual space requirements of each OS and a swapfile, so I've got what I need, muchos thankos :mrgreen:

<edit> I keep thinking of little things to ask; Does the linux swap section need to be a separate partition? and similar question - does windows need a swap file separately or will that be included in the 5gb install space?  

Also, what exactly goes into the root partition? Is it just ubuntu itself or do the programs I install need to be allowed for as well?

heh, it all starts off sounding so simple, then when you start thinking too much about everything it turns confusing (if i just went and did it it'd probably be fine ;) )

---

### Post by gn2 on 2006-10-10
> **mahy said:**
> No you're not. Windows can only access Linux partition using 3rd party utilities and i've never seen a write support. 

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by tuqann on 2006-10-11
Wouldn't work for what I have. I have to have a full-fledged winXP cuz wireless certificants and VPN client are very fragile, running XP on a virtual machine won't do the trick. On the other hand, I'm installing Ubuntu for extensive programming work, includes playing with the Shell. I don't want a VM to ruin it for me.

---

### Post by tuqann on 2006-10-11
Any idea is my SATA drive would give Ubuntu's installation problems? I got an external USB Floppy drive when I installed winXP (It needed OEM files and would not read it from anywhere other than a floppy). Will Ubuntu need OEM or some other files to recognize the harddrive when installation begins?

---

### Post by Rhubarb on 2006-10-11
Ubuntu can recognise most SATA disks fine without having to use a SATA controller floppy disk.  - I've installed it here on my 100GB SATA drive laptop, piece of cake.

---

