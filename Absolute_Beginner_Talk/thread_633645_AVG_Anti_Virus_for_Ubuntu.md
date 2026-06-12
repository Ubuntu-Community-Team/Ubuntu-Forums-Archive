---
title: "AVG Anti Virus for Ubuntu"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-12-06
Hello Ubuntians................

I just downloaded AVG antivirus  and I get the following message when trying to install:

Error: Wrong architecture 'i386'

This package contains the binary release of AVG Anti-Virus  for x86 Linux and graphical user interface avggui.

I guess this is because I'm using a 64 bit version of Ubuntu....

What can I do.....

Thank you

---

### Post by PeterJS on 2007-12-06
Smile, laugh, forget about AVG, go read up on Linux security from some of the stickied threads over the in the servers and security subforum, and then sit smugly and be glad you're not running windows.

---

### Post by lentomies on 2007-12-06
But I am running windows. Actually, I got a tri-o/s systems. Each HDD has its own o/s in a private mobile rack. However, I need a key to turn on the drive of the O/s I want to use.

I have another HDD internally where things get dumped. It a virus got in there while using Ubuntu and then accessed XP when I have that up and runnning I think I could be screwed....

So I believe in preventative maintenance and avoiding problems  since it's the smart thing to do.

Can someone else help me please?

---

### Post by CaptainInsaneO on 2007-12-06
lentomies, is the deb file you used located at [http://free.grisoft.com/filedir/inst/avg75fld-r49-a1130.i386.deb?](http://free.grisoft.com/filedir/inst/avg75fld-r49-a1130.i386.deb?) If so, that should work for your architecture, 32 bit is forward compatible with 64 bit. In other words, 32 bit apps should work fine on 64 bit processors.

Try that deb file, if it doesn't work, I don't have a fix for you :(

---

### Post by lentomies on 2007-12-06
CaptainInsane, I just downloaded and confirmed that it was the same URL. But I got again the same error message. The program installed on my Dell but not this PC...

Here are the specs of my machine if it helps.



Motherboard		
Intel DQ965GFEKR
Processor		
Intel Core 2 Duo E4500
Memory		
G.SKILL 2GB (4 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit 
Hard Disk Drive		
Seagate 300/SATA Barracuda 3.5" Internal HDD - Two (2) units	ST3500641AS-RK	Seagate
DVD/CD Burner w/lightscribe		
20x 8x 8x / 20x 6x 8X/ 12X / 16x / + 48x 24x 48x E-IDE DVD-Dual, support LightScribe, DVD-RAM, Double Layer DVD+/-R9, SMART-BURN, SMART-X, ABS® mechanism.	LH-20A1L	Lite-On IT Corp.
Mobile Rack		
SATA aluminum mobile rack black w/dual fan and anti-shock absorber system	KF-812-BK 	Kingwin
Tower Case		
ATX Mid-Tower Computer Case w/450 Power	TC3J-4050	PowerUp
Multi Card Reader		
64 in 1 USB 2.0 Internal Card Reader/Writer	CRW-UINB	Sabrent
5.25” Drive Bay Storage Box		
5.25” Drive Bay Storage Box	SKU 336049	CompUSA
Cooling Fan		
Cooling Fan, 120mm, Sleeve bearing, 3 pins, 4 pins - Two (2) units	FD12025S1L34	Masscool

---

### Post by CaptainInsaneO on 2007-12-06
Here, try this thread I found: [http://ubuntuforums.org/showthread.php?t=622967](http://ubuntuforums.org/showthread.php?t=622967)

---

### Post by lentomies on 2007-12-06
CaptainInsaneO,

Thanks once again!!!! By the way on my Dell machine I can run a scan but not an update.

When I try to get the latest virus definitions I get error message:

"Update process failed.
Reason: Sorry you do not have permission to excute avgupdate"

Do you know a work around?

---

### Post by g2g591 on 2007-12-06
won't sudo work? (sudo whatevercommandistoupdate) or gksu command (if its GUI)

---

### Post by Dr Small on 2007-12-06
> **lentomies said:**
> CaptainInsaneO,

Thanks once again!!!! By the way on my Dell machine I can run a scan but not an update.

When I try to get the latest virus definitions I get error message:

"Update process failed.
Reason: Sorry you do not have permission to excute avgupdate"

Do you know a work around?
Use sudo ;)

---

### Post by SOULRiDER on 2007-12-06
Try doing 
```
sudo avgupdate
``` in a terminal. 
If that fails open AVG as root and try updating. I dont know what the command for AVG is since i dont have it installed, but lets supose its "avg", in that case do this.

Press alt + f2 and type:
```
gksu avg
```

Good luck!


PS: If a virus got in your pc while using ubuntu it wouldnt be able to affect XP since it wouldnt even run on ubuntu. In other words, a virus will only run in xp, so theres no need to protect yourself from a programt hat cant even run!

---

### Post by CaptainInsaneO on 2007-12-06
I've had the same update problem before. I believe I fixed it by running the avg gui as root (use sudo).

If that doesn't work, try to update it manually. I'd give you the info on how to do that but I'm about to take the first exam for my MCSE and don't have the time right this moment. :( Try googling it or looking at the avg linux user's manual [here]("http://free3.grisoft.cz/filedir/doc/LINUX_GROUP/AVG_Free_for_Linux/avg_afl_uma_en_75_1.pdf").

P.S. Sorry I'm so slow, everyone beat me to it. :)

---

### Post by daimaru on 2007-12-06
personally i never liked avg because it rarely has updates + on access scanning ?? well i thing you can enable it to on avg, but i still prefer antivir from avira.
got antivir running with avguard (scanning while you access files). the only problem is that you have to shutdown apparmor to get kazuko.ko to run (which is needed for on access file scanning).
but since i never figured out how to really configure apparmor i am happy just using avguard.

---

