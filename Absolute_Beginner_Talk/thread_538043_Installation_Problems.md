---
title: "Installation Problems"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by agtjones on 2007-08-29
Hi,

This is my first post so please go easy on my because i'm sure this has been asked hundreds of times before.

I've just place an order this evening for a new PC:

Intel Core 2 Duo E4500 "LGA775 Allendale" 2.20GHz (800FSB) - Retail
Scythe Samurai Z Rev.B CPU Cooler (Socket 478/754/939/940/AM2/LGA775)
Asus P5N-E SLi nForce 650 (Socket 775) PCI-Express DDR2 Motherboard
OCZ 2GB (2 x 1GB) PC2-6400C4 Dual Channel Platinum Revision 2 XTC Series DDR2 (OCZ2P800R22GK)
OcUK ATI Radeon X1950 Pro 512MB GDDR3 HDTV/Dual DVI (PCI-Express) - Retail
Corsair HX 520W ATX2.2 Modular SLI Compliant PSU (CMPSU-520HXUK)
Western Digital Caviar RE 250GB 2500YS SATA-II 16MB Cache - OEM
Pioneer DVR-112DBK 18x18 DVD±RW Dual Layer ReWriter - (Black) OEM
Lian-Li PC-7 PLUS II Aluminium Midi-Tower Case - Black

And would like to run Linux Ubuntu as the O/S.  I currently run a HP Pavillion with Windows XP which I was trying to convert to Ubuntu today with absolutely no joy what so ever.  I was following the instructions from the below link and have to admit that I clear missed something that might seem obvious to many people looking at this forum.

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

Anyway to cut a long stort short I am looking to run Ubuntu on the new system and am after some advice on the simplist way of installing it (my old PC had no floppy / CD drive hence the installation method in above link).  Please NB:  I am a complete novice when it comes to computers this will be my first build and all my colleges who have pretty nice DIY PC's themselves (big gamers) all think i'm crazy as they say Linux is v. geeky and difficult to get to grips with (not my words, I apologise on their behalf!) and therefore would be almost impossible for me to install with greater knowledge.

Although I haven't got this PC yet and am unlikely to be in a position to try loading Ubuntu before Sunday anu advice would be greatly appricated.  The problems I had with my current PC where not understanding how to set up the directories so that GRUB (?) would work and therefore could get further that that.  Hopefully the new build will not be so difficukt as it will has no o/s from the get go.

Thanks in advance
Andy

P.S. I have seen a note about ATI X series graphics cards being an issue in there a version I am better to try and install due to this?

---

### Post by Duck2006 on 2007-08-29
Have a read of this it sould help

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by ts51 on 2007-08-29
I just skimmed over your post, but you could probably take out the old computers HD, put it in your computer with a cd drive, and set it up the way you want it. Take the HD and put it back in your old computer. I don't know if it will work, but it possibly could.

---

### Post by svalding on 2007-08-30
Nah, doing stuff like that will mess up the HAL. 

Your best bet will be to download a live cd, and use it to install from. Use it in a "live environment" first, to get a feel for linux, and how the filesystem and things work. Once you do that, click the install icon on the desktop and your off! 

If you plan on dual booting, install XP first, and then try to install linux. It will give you the option to resize the current partition, and then you can install ubuntu onto the free space it creates, and as for GRUB, the install will do 'er for ya.

---

### Post by Duck2006 on 2007-08-30
[http://video.google.ca/videoplay?docid=-6104490811311898236&q=dual-boot](http://video.google.ca/videoplay?docid=-6104490811311898236&q=dual-boot)

This is worth a look

---

### Post by evolving_monkey on 2007-08-30
I used Partition Commander 10 pro to set up partitions and left a 30gig empty spot to load Ubuntu on. When I installed Ubuntu Feisty Fawn 7.04 I simply checked the box that said install to the largest frees pace and it worked with no problems. I was a noob to Ubuntu at the time also. It set everything up on its own and it worked great. From there I was able to 'get under the hood' and figure more stuff out.

Dual booting with Windows XP was very similar. I set everything up with the windows install cd (partitions and free space, also remember to install windows first) and again told Ubuntu to install to the largest free space. The only time I've run into problems is when I forget that you can only have 4 primary partitions on a hard drive. Then it would wrap the boot partition with an ntfs partition in an extended partition and I couldn't write to the ntfs partition even with ntfs-3g.  (that was an experience that reminded me how good I can be at screaming profanity)

---

