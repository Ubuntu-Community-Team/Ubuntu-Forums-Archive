---
title: "Weird display problems.."
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Clock Sabre on 2006-05-09
I hope posting pictures is allowed here.. I haven't seen any posted yet o.o

Anyways, I figured the best way for everyone to understand my problem would be by taking pictures of my desktop when it does the weird display problems..

[IMG]http://img439.imageshack.us/img439/1641/screenshot0lw.png[/IMG]
The top bar basically gets covered and will stay like that.. making opening things a real challenge. Also, little lines appear over the screen sometimes.

and..

[IMG]http://img435.imageshack.us/img435/3827/screenshot16zw.png[/IMG]
This is a perfect example of what I was trying to explain with the lines.. when I load a website or open a program, these lines (not always white) will just appear all over the screen.. and cover the top bar, as well. 

(I apologize for the ad in that second one... 'Tis stupid, yes. Anyways..)

So, does anyone know what the problem could be, and how to resolve it?

---

### Post by uzi09 on 2006-05-09
wow, that really is odd.

i'm curious, has it been like this since first install, or just started up randomly?

also, what version of ubuntu are u using?

---

### Post by Clock Sabre on 2006-05-09
This is from the first install. And it's always like this.. I've reinstalled it a total of 4 times now, thinking that could be the problem, and yet it rises up each time. 

I'm using Ubuntu 5.10, the breezy badger version. And I know the cd I installed it with is perfectly fine, since I installed ubuntu on my laptop and it works fine. So I'm just assuming it's some hardware problem on my desktop.

I'm using an AMD64 athlon processor as well.

---

### Post by richbarna on 2006-05-09
Wow that's weird !!
What graphics card have you got?
and on the laptop?
Have you tried different drivers? (Nvidia or ATI, Vesa)

---

### Post by Clock Sabre on 2006-05-09
Well, I believe I have some driver called "SiS" on my desktop.. Excuse my ignorance in that department.
The driver on my laptop is trident? I think.

Oh, and I failed to mention.. I'm running the i386 version on both computers.

Also, I noticed this person had the *exact* same problem as I did.
[http://ubuntuforums.org/showthread.php?t=103373](http://ubuntuforums.org/showthread.php?t=103373)

---

### Post by Clock Sabre on 2006-05-09
Here's some more specs on my desktop, if it helps at all..

Compaq Presario SR1550NX
200 gb harddrive (I'm running solely linux on a 90gb partition, with a 1.5 gb swap space partition)
512MB PC3200 memory
AMD Athlon 64 Processor

And here's the specs for my laptop:

HP Pavilion N5415
10 gb harddrive (Yeah, it's 5 years old :P) (It's solely running linux, for obvious reasons)
128MB memory
AMD Duron Processor

---

### Post by uzi09 on 2006-05-09
yeah, i'd definately recommend giving dapper a try. theres only about 20 more days before the final release. i'm currently using it myself and it's working great. haven't really had any problems. plus there is a major upgrade on a daily basis, so they're really working hard on this stuff.

also, their hardware support is phenominal from one version to the next!

give it a try - even if it has to be the live cd.

heres a link to a GREAT guide that'll run you through how to upgrade your version of ubuntu without having to uninstall/burn cds/reinstall :D

[http://easylinux.info/wiki/Ubuntu#Upgrading_Ubuntu](http://easylinux.info/wiki/Ubuntu#Upgrading_Ubuntu)

---

### Post by nalmeth on 2006-05-09
dunno really,
try changing your video driver to vesa with :
sudo dkpg-reconfigure xserver-xorg

you will lose any 3D functionality you had before though

I would also suggest dapper if you are up for it! Using it on my laptop and PC!

---

### Post by Clock Sabre on 2006-05-10
Well, I followed your suggestions and just decided to dive in and try Dapper Drake... And from what I can see, it worked. The problem just seemed to disappear as soon as dapper loaded. Amazing.

I have to add.. dapper drake looks wonderful. o.o

---

