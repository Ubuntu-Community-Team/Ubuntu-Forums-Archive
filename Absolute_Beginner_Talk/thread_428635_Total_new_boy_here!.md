---
title: "Total new boy here!"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by teh paul on 2007-04-30
Hi all,

As you can guess by the title, I'm a complete and utter n00b when it comes to Linux! I mate of mine has been using it for years and said on several occasiona that I should try it!

At the mo, I'm currently downloading the Desktop version with the 3 year jobbie. My question though (since my mate aint around), is will it run OK on my laptop? The specs are...

Acer Aspire 5101AWLMi
AMD Turion 2 Ghz, 512kb L2 cache
ATi Radeon Xpress 1100
120GB HDD (I think it's actually 2 seperate HDDs...)
512MB DDR2
802.11 built in wireless LAN

Will there be any issues that I should know of?

Cheers in advance dudes and dudettes! :D

---

### Post by Petar Marjanovic on 2007-04-30
I don't see any problems with your system configuration. But I don't really know whether you can run Beryl and other graphical vista-**** (like 3D-Cube).

---

### Post by starcraft.man on 2007-04-30
Your spec seems fine to me to run Ubuntu, probably even Beryl. I'm not sure what you mean by downloading 3 year jobbie? You mean 6.06 with LTS? You can run any of the desktop versions if you like.

You may have a bit of trouble with wifi, its always been a bit problematic to get that to work so have an ethernet plug to get internet while ya try and set it up. I think its a little bit easier in Feisty to get wifi, choice is yours which version you put in though.

---

### Post by LaRoza on 2007-04-30
It should run perfectly. However, I do not know about the wireless LAN, Feisty should recognize it as far as I know.

To make sure, try the live disk first, or install on a separate partition. 

Welcome to Ubuntu!

---

### Post by teh paul on 2007-04-30
Sorry, forgot to mention that I'm running XP and want to be able dual boot. 

And Starcraft, yes, the 6.06 version I'm downloading!

---

### Post by jecahn on 2007-04-30
I'm running Feisty on a Pentium 3 @ 600mhz.

If I can get it running competently on that machine you'll have no problem. One of my favorite things about Ubuntu is the fact that is makes old hardware usable again...

---

### Post by lyceum on 2007-04-30
Looks like a good box. I have 7.04 on my laptop and it rums better than Vista (I dual booted). It is faster and more efficent. Once up, go to Systems/Preferances/Desktop effects. If you can get that (very bad) vesion of Compiz to work, shut it down and got to Systems/Administration/Synaptic Package Mangare and use the search for Beryl. Load it for MUCH better 3D effects. 

Enjoy!

-edit-
also, check out psycocat's Ubuntu page (there is a link in my signature) for lots more usful info.

---

### Post by LaRoza on 2007-04-30
Dual booting should be easy. 

You can partition your hard disk before installing or resize it during the installation. Grub (Like the MBR), should recognize XP and add it too the boot menu.

You should also backup any thing you don't want to lose. Resizing partitions can cause data to be lost.

---

### Post by starcraft.man on 2007-04-30
Ok, that is simple to make a dual boot. Make sure you have at least 10 GB free on your hard drive. When you get to the gparted partitioner. Make a 6 GB partition for the root directory (/ ), make a 2-3 gb partition for swap file. That should be it. If you want to store your files seperate, make a partition for /home with as much space as you wish to store.

So you should have in the end:
- XP install
- 6 GB /
- 2 GB swap
- Rest /home

Then install to the root drive /. Grub at the end will detect your xp install and let you install grub to the Master boot record, say yes and you'll be able to boot both OSes.

---

### Post by teh paul on 2007-04-30
Thanks all! I've finished downloading, so I'm off to make a CD and see how we go from there!

---

### Post by jvc26 on 2007-04-30
You may have some issues with your ATI gfx, as they are notoriously difficult with Linux, however, its not unresolvable, so don't fret too much,
Il

---

### Post by kosson on 2007-05-01
This ATI card gives me headaches !

teh paul, I have the same machine and I haven't got 3d support working with radeon xpress 1100.

I know it will take me a lot of time to figure it out !

I believe this laptop was built specially for windows... it's not an easy ride with linux. But, I'm stubborn.:)

---

