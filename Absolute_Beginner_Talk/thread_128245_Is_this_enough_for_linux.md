---
title: "Is this enough for linux?"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by phantom on 2006-02-11
I got some old hardware laying around and I would like to make a file server out of it, would it be enough for it or isn't worth the hassle?

P3-E slot1 733Mhz
QDI Advance5 133/E Motherboard
2X 128MB Kingston PC133
300W Power Supply
8MB Nividia Vanta AGP 2X
Realtek 100MB PCI Nic

I would need to buy a hard drive for it, so I thought about putting a 300GB on either a PCI Sata controller or a PCI Raid card so that I can make the mobo support the drive.

It would mainly serve as File server for divx/mp3 and as a PVR for my Sat receiver over Ethernet.

OS would Ubuntu 5.10.

---

### Post by heimo on 2006-02-11
To me it looks good. Though I don't know about performance requirements for recording video. If you can run it without X, even better - lot's of memory is saved for disk cache. I ran email server / web server with 128MB and Duron 700MHz - it was perfectly fine.

---

### Post by phantom on 2006-02-11
I'll use X during the setup stage but it won't be running during normal operations, maybe I'll fire it up when I need some administration help, but anyway it won't be KDE ;)

For video recording I would imagine that only the speed of the harddrive counts as there is no encoding to be done, that's done by the Sat Receiver.

Actually the Sat Receiver won't even know it's an external server as I'll mount it's /hdd directory through NFS on the linux server.
Sat Receiver is a Dreambox which is running embedded Linux.

---

### Post by bikeboy on 2006-02-11
Should be plenty of power for a file server. As you say it won't en/decode so really it'll just be like NAS.

---

### Post by cotcot on 2006-02-11
I have no experience with servers. Maybe it helps knowing that i can normally play DVD's on my test PC (P3 500 in my signature)

---

### Post by phantom on 2006-02-11
[QUOTE=cotcot]I have no experience with servers. Maybe it helps knowing that i can normally play DVD's on my test PC (P3 500 in my signature)[/QUOTE]

Thanks :cool:  that is indeed some good information.

I have set up Ubuntu now on that machine running on a VERY old 8GB drive to see how it runs and I must say it's amazing how fast it all runs, even stuff like OpenOffice2 just opens in a snap.

I can clearly see that the old HDD is the bottleneck now, so I'll be out buying a nice HDD, Controller and maybe some nice housing for it today.

It's just a shame that I'm unable to use Linux for daily usage due to hardware incompatibility on my Laptop, and a printer that isn't recognised with all it's funtions like CD/DVD printing, I think it would scream :p

---

### Post by heimo on 2006-02-11
[quote=phantom]
I have set up Ubuntu now on that machine running on a VERY old 8GB drive to see how it runs
[/quote][quote=phantom]
I can clearly see that the old HDD is the bottleneck now, so I'll be out buying a nice HDD, Controller and maybe some nice housing for it today.
[/quote]
You can expect speed increase of around 3-6x for disk operations, of course the effect on whole system won't be so much, but it's definitely noticeable.  If it's parallel ata disk (not serial ata) be sure to use 80 pin "ultra dma" cable.
[http://www.pcguide.com/ref/hdd/if/ide/confCable80-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCable80-c.html)

---

### Post by phantom on 2006-02-11
Don't worry, I don't think it'll even support that, it's old from 1998 :$

I just added a Pinnacle PCTV card in there, through the inputs I connected the Sat Receiver and installed MythTV, it's working !!

This machine is turning out to be a very nice media center pc, I thought it would be a close one to get it up and running but I'm amazed with the power.

---

### Post by fmo on 2006-02-13
If you want to use it as a file server to record some videos you might need to also invest in a Gigabit network card, your 100Mb card will be the next bottleneck after the disk upgrade.

Before buying anything, do some tests, I might be wrong, but you won't exceed 10MB/s of throughput with a 100Mb card.

---

### Post by damianubuntu on 2006-02-13
For what its worth, I'm running 5.10 on a celeron 633 with 256mb and 6gb hdd, and it  runs fine as a desktop box, for internet and office use, though openoffice is a bit slow to start.  I put Suse10 on it first, but that was impossibly slow.  By the way, how did you find out that it was the HDD that was slowing everything up?  Since thats the first thing Im considering upgrading...

---

