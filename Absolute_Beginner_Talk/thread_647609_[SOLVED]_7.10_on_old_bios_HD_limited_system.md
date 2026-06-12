---
title: "[SOLVED] 7.10 on old bios HD limited system"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Momule on 2007-12-22
hello I have a CD with 7.10 on it, 1st  time it ran as live, then I wanted to install to hard drive. Bios error is what I got, can't access that partition. So I reformatted the drive and tried again, now all I get is 

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Build-in shell (ash)
Enter 'help' .....

(initramfs) ide_media[2831]: main: unable to read from '/proc/ide/ide0/hda/media

I cleaned the CD and tried again...shows as above....wont live boot either..
 nothing but BusyBox Message..

System is:
FIC AM39L : a mash together by Tigerdirect and FiC I think..
1 Meg Memory
92 GIG HD
2 CD Drives
 OH yes I am completely a Newbie with Linux systems..
Trying to Learn

Thanks in Advance....

---

### Post by ijason on 2007-12-22
that's weird... i would recommend unplugging the HDs and booting off the live cd. i think the live cd will run even without a physical hard drive to mount, and that would eliminate a flaw on the cd as the source of the problem. 

are you familiar with working with your computer's hardware?

---

### Post by Momule on 2007-12-23
Yes I am comfortable with hardware.. Operating systems are my doom.. understanding them that is...I build my own systems..  
 I thought it must be something with the commands in ubuntu, that i needed to get it go 
I know read the ... manual..:lolflag:.. guess I better get one.. 
thanks for responding...

---

### Post by Josh1 on 2007-12-23
My guess from the error message is that it cannot read/find/does not have permission to access the harddrive you wish to format/partition to. Have you tried another harddrive?

---

### Post by Momule on 2007-12-23
Well No I haven't, it worked Once, I think the Bios limit is holding me back, I know in Windoze it had to have a program called E-Z Bios to format and see the full drive. 

Just thought there might be a  program something like that in ubuntu ?

Or maybe a command or two I could use to get it going...

---

### Post by louieb on 2007-12-23
> **Momule said:**
> ,,,1 Meg Memory
I guess that a miss print. 
Anyway time to play with boot options...
Try some of these that deal with accessing a hard drive.
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")
Knoppix like Ubuntu is Debian based. most of these are good too.

 
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")

---

### Post by Momule on 2007-12-23
Hey Thanks Guys , this form really works....

ijason thanks ..it works with out the HD..Like you suggested.. at least now I can play with the operating system

louieb thanks for the links and suggestions..maybe now I can get the boot to work and 

Yes a miss print on MEmory.. yep..ME-mory..:lolflag:

really its 1 GIG... Doh... thanks again Guys.. maybe in a year or so, I can help someone?

---

### Post by Momule on 2007-12-24
Hey Guys, Coming from you on the ubuntu machine. Finally got it to going thanks to you, and I forgot Jason1 too. 

Oh I did both suggestions and it worked, if anyone has the same problem.

again thanks  and Merry Christmas fella's     

Now do I mark this as solved or someone else? err where and how ?

---

