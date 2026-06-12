---
title: "[SOLVED] Start 7.10? or give it some time?"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Yamazaki on 2007-10-31
Hi, iam totally new to linux world, first time i ever install a linux distro on my pc, i was recommended to start with ubunto, last few days i been through guides and tutorials .. etc, i wanna make sure good start with the system before i first boot, so i dont "Time to give up linux" early.

I've read somewhere here that 7.10 got some issues, so i was wondering if i should start with 7.04, since its more stable, and give 7.10 sometimes!, i just dont wanna make my start involved issues and problems .. etc, i just need a stable version to start off with.

My pc specs btw:
AMD Athlon 64 X2 3800+ (2x512)
1GB ram
160 HD
7600GT 256mb

One more thing, i got all my H.D Partitions NTFS format, would that be difficult for ubunto to read them?, read somewhere that ubunto read/write Fat32 only!

---

### Post by It_Was_Luck on 2007-10-31
I love Ubuntu 7.10, I haven't (yet) encourntered any problemes and I'm also new to ubuntu, so I recommend going to with 7.10, its the lastest and greatest.

Your computers specs look pretty good, I don't see why there would every be a problem with a computer like that.

And using a program called GParted included in the Live CD, you can format any type of HD, yes NFTS too, just as well as any other one, just create an extended partition and put the main one and the swap partition (and if you wish a home partition) in there.


Hope that Helped.

---

### Post by alwiap on 2007-10-31
i have specs very similar to yours (i used to have x2 3800+ athlon, now i have an opteron and i have a 7800gt) and have installed 6.06, 7.04, and 7.10 and had no problems whatsoever, maybe i'm lucky :)

edit:  i had problems writing to my 2nd hard drive (ntfs) up until 7.04 but by default in 7.10 i was able to write, delete, and modify the drive without doing a thing.  so you might want to think about 7.10 if you don't want to reformat the hard drive like me.

---

### Post by amneziac on 2007-10-31
well personally, ever since i got gutsy, i have encountered problems that i dont know how to fix. My opinion is to wait a little bit more so many of the bugs get fixed.

---

### Post by forestpixie on 2007-10-31
I've not had many problems with 7.10 and have been running it since it was beta, any problems I've had have been of my own making :)

you could go with 7.04 if you want - but I can't say I would. If you can do it why not download 7.10 and burn it as a livecd and check out you're hardware with it - if you've problems try 7.04.

they'll both read NTFS partitions - but you'll have to have a partition suitable for it to run - and that doesn't include NTFS.

Have you seen the [psychocat]("http://www.psychocats.net/ubuntu/") site - it's a good start

There were some issues with 7.04 64bit I believe, but can't be sure

---

### Post by Inxsible on 2007-10-31
> **Yamazaki said:**
> Hi, iam totally new to linux world, first time i ever install a linux distro on my pc, i was recommended to start with ubunto, last few days i been through guides and tutorials .. etc, i wanna make sure good start with the system before i first boot, so i dont "Time to give up linux" early.

I've read somewhere here that 7.10 got some issues, so i was wondering if i should start with 7.04, since its more stable, and give 7.10 sometimes!, i just dont wanna make my start involved issues and problems .. etc, i just need a stable version to start off with.

My pc specs btw:
AMD Athlon 64 X2 3800+ (2x512)
1GB ram
160 HD
7600GT 256mb

One more thing, i got all my H.D Partitions NTFS format, would that be difficult for ubunto to read them?, read somewhere that ubunto read/write Fat32 only!7.10 is much better in terms of recognized hardware, so I would suggest you go with 7.10

I had 7.04, and it was great, but when 7.10 came out, I installed the 64 bit version and everything worked out of the box. Suspend and hibernate which did not work in 7.04 for me, started working too !!!

About your partitions, you will need atleast 2 partitions in EXT3 format to install Linux (one for root partition and another for home). Its good practice to have a separate home partition even though you can do without one. You will also need a swap partition. Apart from those 3 all other can be NTFS and 7.10 will read and write to them without any problems.
7.04 will be able to read them but not write to them unless you install the ntfs-3g package.

---

### Post by jwhitecl on 2007-10-31
Well, I have a Inspiron 1501 and have run both 7.04 and 7.10. When I installed 7.04, just about everything worked great. My ATI drivers installed just fine, but I had to poke around with ndis to get my wireless to work. Now, I have 7.10 and I had a several small issues after installation, but they were all easy to resolve. You will probably have the same amount of problems with either version, and being that 7.10 is more current, I would go with that one.

---

### Post by aks44 on 2007-10-31
I had absolutely NO problems with 7.04 (and it was the very first time I installed a Linux distro).

Today I just installed 7.10... OMG I really wish I didn't. I "only" have one serious (display) issue, but in like two hours I came across uncountable "minor" bugs (Adept aborting without apparent reason, ...)

Better use 7.04 at least it works fine, just my $0.02.

---

### Post by Jerry N on 2007-10-31
Install 7.10.  If you have major problems, flush it and install 7.04.  Installing Ubuntu is no big deal, no activations or anything like that.  Either one will probably start up with default video drivers and give you the opportunity to install the real Nvidia drivers.  

Jerry

---

### Post by Yamazaki on 2007-11-01
Thank you all, i guess i'll start with 7.10, psychocats is also a great tutorial site, thanks forestpixie.

---

### Post by forestpixie on 2007-11-01
no problem - good luck and can you mark thread solved :)

---

