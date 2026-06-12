---
title: "New Intel machine running Ubuntu"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by nowist on 2006-08-22
hello:
i am interested in running Ubuntu on my homemade computer that I am wanting to build. The configeration for the Intel based machine I want to build is posted at the URL belwo and I am curious if all the components are Ubuntu/ Linux freindly. 

[http://www.hearightnow.com/homemadeCPU.xls](http://www.hearightnow.com/homemadeCPU.xls)

thanks:
:KS

---

### Post by Jerk on 2006-08-22
Here... for everyone's sake.

> 	
**motherboard**	ASUS P5B DELUXE/WiFi-AP INTEL 965 CHIPSET
**processor**	Intel Core Duo Processor T2400 1.83GHz 2MB CPU
**CPU fan**	THERMALTAKE CL-P0024
**power supply**	STARTECH - 600w eps12v
**video card**	GeForce 7600GS
**audio card**	Turtle Beach Riviera 5.1
**TV Tuner**	ATi TV Wonder Elite PCI Card with FM/TV Tuner, Coaxial, S-Video
**drive (x2)**	Seagate Barracuda 160GB 7200 RPM SATA 3.0Gb/s
**DVD+/- RW (x2)**	LaCie 16x DVD+/-RW IDE/ATAPI DL Internal with LightScribe
**RAM**	KINGSTON HYPERX 2GB  DDR2 800MHZ
**casings	**TP-8854 Enclosure Rack Mount 4U IPC Computer Chassis
**monitor**	ViewSonic VP930B 19" LCD Monitor
	
	


---

### Post by nowist on 2006-08-23
thanks Jerk

---

### Post by Jerk on 2006-08-23
No problem. .xls files are just a pain in the butt to load over something that can be viewed directly.

As far as compatibility, as far as I know (Which isn't far at all... a few cm), everything listed is compatible. Can someone put me in my place?

---

### Post by matty429 on 2006-08-23
I have the Gigabyte 965p-DS3

I cant boot any cd ..I've also tried booting from a usb cd ..that didn't work....

Edgy Knot 1 wont work as well

What is odd is I had Dapper running from a previous install on a 975x board, I Swapt in the 965 board and it boots fine...
I just can't re-install, my current install after motherboard swap can't see my cd drive..

I'm sure the next build of edgy will fix this issue...

---

### Post by TFX360 on 2006-08-23
The wireless cards in Lunix (well in Windows too ofcourse) can give you a hard time. Double check. Get the driver / inf name and double check that too. I dunno about this (integrated?) card.


Kind regards,


TFX

---

### Post by kwanghui on 2006-08-23
I was planning to buy this motherboard but there is a serious problem because of the jmicron controller, which doesn't work with the DVD and IDE drives. ie you will need to install from external USB CDROm or network install. sigh.

search for p5b on the ubuntu forums to see this:

[http://ubuntuforums.org/showthread.php?t=236802&highlight=p5b](http://ubuntuforums.org/showthread.php?t=236802&highlight=p5b)

---

### Post by viskonde on 2006-09-27
so.. for a gigabyte Ds3, there isnt any solution yet?
i've bought one, and i cant boot the livecd to install.. :(
it breaks when is loading.. 

someone know how to install 6.06 in this gigabyte?
any patch or something like that?


[[]]

sorry my english

---

### Post by rbmorse on 2006-09-27
The ASUS P5B motherboard is built around the Intel 965/ICH8 chipset. Not sure about the other one, but I suspect it is too.  The Intel 965/ICH8 chipset does not support Parallel ATA (IDE) devices, so ASUS (and I suspect Gigabyte) adds a third party IDE/RAID controller for PATA support, usually a Jmicron chip. 

For Linux users that was not a good choice. Linux kernel support for the Jmicron IDE controller doesn't happen until 2.6.18 which was just released a week ago. It will take time for it to percolate into the distributions. 

The next K/Ubuntu will have the 2.6.17 kernel so it won't work with motherboards built around the Intel 965/ICH8 chipset either, unless there is some last-minute backporting going on. 

Rumor is that you can install K/Ubuntu onto a 965 based machine from a USB or SATA optical drive, but I haven't tried it. SATA optical drives have their own problems with Linux and are not recommended.

---

### Post by viskonde on 2006-09-29
ubuntu 6.10 should came out on october rigth?
do you know if it will suport this boards/chipsets?

if it does.. i can wait a month :P

[[]]

tks

---

### Post by rbmorse on 2006-09-29
As t stands right at this minute, Edgy still has the 2.6.17 kernel which does not fix the lack of support for the Jmicron IDE controller on on Intel 965 based motherboards.  

I have seen some rumors that the situation is being addressed and fixes will be included in Edgy by the time it is released, but I haven't seen anything definitive. 

Were I in your postition I would be hopeful but not convinced.

---

### Post by StefanSteinheimer on 2006-10-03
Well, the JMicron controller is working in the current daily iso of edgy, but ich8 support is now broken (working in older releases). That means PATA drives do work, but SATA drives are not recognized when they are connected to the ich8-controller. This will hopefully be fixed soon.

---

### Post by viskonde on 2006-10-19
well , 
Ubuntu 6.10 is almost there..

sombody knowes if it runs in this Boards?

or like 6.06 it crashes on loading ide?

---

### Post by viskonde on 2006-10-28
hey

now that 6.10 as arrive...

does it work on this motherboards?

---

### Post by Pravus Pestis on 2006-10-28
viskonde, Edgy does indeed work with these motherboards. I've been running it on a P5B-Deluxe (no wifi) for a few weeks now. It's somewhat unstable, but as previously mentioned the real support won't show up until 2.6.18. It's certainly usable though. 

Cheers.

---

### Post by viskonde on 2006-10-28
ok..
is because i cant run 6.06 on my DS3..

when im loading LiveCD , it 'crashes' when is detecting ide or something like that..

so, on wednesday i wil download and try it ;)

---

### Post by miltoda on 2007-10-11
I have the same problem with my home built PC
I have a ds3, E4300, Pata DVD and a SATA HD and both gusty and feisty install cds wouldn't work.

---

### Post by miltoda on 2007-10-11
> **viskonde said:**
> so.. for a gigabyte Ds3, there isnt any solution yet?
i've bought one, and i cant boot the livecd to install.. :(
it breaks when is loading.. 

someone know how to install 6.06 in this gigabyte?
any patch or something like that?


[[]]

sorry my english

I have the same problem...any fixes?

---

### Post by steve.horsley on 2007-10-11
try starting your own thread - this one finished a year ago

---

