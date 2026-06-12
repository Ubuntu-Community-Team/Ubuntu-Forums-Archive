---
title: "Why can't I install Ubuntu (Dapper or Feisty)?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by stpieraf on 2007-03-20
Hello, everyone!

Well, I'm up to at least attempting to begin using Ubuntu for the first time. And I must say, I'm already off to a shoddy start. 

If I may be so bold, to any of the dev team, if you really want to break the barrier of entry for users, getting to the installation screen for the OS should never be an issue. It should be flat out brainless with no chance of error, save for a broken CD-ROM drive (Even then, it should say so. :) ). I'm sure there are many old M$ users who aren't terribly proficient or knowledgeable of Linux who are attempting to try this out, then getting discouraged when there are complications just getting to the first step of an installation.

I've attempted to at least run the live CD or install with both Feisty and Edgey, both amd64 and i386 versions (Just for the heck of it) and it always yields similar results. I can either get to the Ubuntu Progress bar (Just after you hit the "Start or Install Ubuntu" option from the disk), where it shall hang for eternity, or return various errors. With Edgey, I tried a readme that got me to the starting screen on live CD, only  to have it crash whenever I did.. well anything. 

I believe it may be related to my setup, but I am not sure what exactly I need to do to get the ball rolling. I was hoping someone would be able to point me in the right direction. Here's my computer's setup:


Processor(s)	 

Number of processors	1
Number of cores	1 per processor
Number of threads	1 (max 1) per processor
Name	AMD Athlon 64 3200+
Code Name	Venice
Specification	AMD Athlon(tm) 64 Processor 3200+
Package	Socket 939
Family/Model/Stepping	F.F.0
Extended Family/Model	F.2F
Brand ID	4
Core Stepping	DH-E3
Technology	90 nm
Core Speed	2010.4 MHz
Multiplier x Bus speed	10.0 x 201.0 MHz
HT Link speed	1005.2 MHz
Stock frequency	2000 MHz
Instruction sets	MMX (+), 3DNow! (+), SSE, SSE2, SSE3, x86-64
L1 Data cache	64 KBytes, 2-way set associative, 64-byte line size
L1 Instruction cache	64 KBytes, 2-way set associative, 64-byte line size
L2 cache	512 KBytes, 16-way set associative, 64-byte line size

Chipset & Memory	 

Northbridge	NVIDIA nForce4 rev. A3
Southbridge	NVIDIA nForce4 MCP rev. A3
Graphic Interface	PCI-Express
PCI-E Link Width	x16
PCI-E Max Link Width	x16
Memory Type	DDR
Memory Size	2048 MBytes
Memory Frequency	201.0 MHz (CPU/10)
CAS# Latency (tCL)	2.5 clocks
RAS# to CAS# (tRDC)	3 clocks
RAS# Precharge (tRP)	3 clocks
Cycle Time (tRAS)	8 clocks
Bank Cycle Time (tRC)	11 clocks
DRAM Idle Timer	16 clocks
Command Rate	2T

System	 

System Manufacturer	 
System Name	 
System S/N	 
Mainboard Vendor	 
Mainboard Model	NF-CK804
BIOS Vendor	Phoenix Technologies, LTD
BIOS Version	6.00 PG
BIOS Date	12/29/2004

Memory SPD	 

Module 1	DDR, PC3200 (200 MHz), 512 MBytes, Corsair
Module 2	DDR, PC3200 (200 MHz), 512 MBytes, Corsair
Module 3	DDR, PC3200 (200 MHz), 512 MBytes, Corsair
Module 4	DDR, PC3200 (200 MHz), 512 MBytes, Corsair

Graphics:

GPU: Nvidia Geforce 6600
Type: PCI-E 16x

Other:

Onboard Sound
Onboard LAN
Raptor SATA 36GB, 10k RPM
Logitec G15 Keyboard (USB)
MS Habu Razor Mouse (USB)


The chipset and GPU seem to be the most likely candidate's for a problem, but I've seen stranger back in the old days when I tried to install Red Hat: A keyboard was my problem.. So really, it could be anything.

Any help will be greatly appreciated. :confused: 

Thanks in advance!

---

### Post by machoo02 on 2007-03-20
Hi,

Sorry to hear that you are having so much trouble.  Your set-up doesn't seem to be that exotic.  I noticed that you listed Feisty as one of the disks that you tried.  For someone new coming into Linux, it is generally not recommended to try installing the version that is currently under heavy development as there is a strong chance of failure.  Have you tried the latest stable release (6.10 - Edgy Eft) yet?

---

### Post by stpieraf on 2007-03-20
Hello, and thank you for replying.

Yes, I have. And that's what led me to try Feisty. I figured if something I needed was missing from Edgy, then maybe what I need would be in Feisty, even if it was in beta.

---

### Post by seshomaru samma on 2007-03-21
You can post some of the errors here 
Perhaps someone will be able to help you

Have you tried installing with an alternate CD (a command -line install ,needs less RAM and often solves many installtion problems related to VGA cards )?

---

### Post by mcduck on 2007-03-21
Did you check MD5 sums for the images when you downloaded them (before burning to disk)? And have you tried to check your CD's for errors? The option for that is in the first boot screen..

---

### Post by stpieraf on 2007-03-21
Thank you all for the replies. To answer:

> **seshomaru samma said:**
> You can post some of the errors here 
Perhaps someone will be able to help you

Have you tried installing with an alternate CD (a command -line install ,needs less RAM and often solves many installtion problems related to VGA cards )?

I'm not getting any errors. I get the image of "Ubuntu" with the yellow progress bar flickering in and out, going back and forth, forever.... There's no error text at all poping up.

Command line install? I've never done it. I don't know where to begin. Is it all done at the command line, or does it only do certain steps to get to a gaphical display of installation options? And wont the VGA card STILL be a problem once I get the files onto my HD, because if it can't recognize it at install, how is it going to recognize it afterwards? 

Incidently, I'm not attempting to install it just yet.. I want to try it first before I wipe away everything I've ever been familiar with: If there's no gaurntee that I'll get something that works at all (let alone, "right for me") once I wipe everything else away, why bother? 

>  Did you check MD5 sums for the images when you downloaded them (before burning to disk)? And have you tried to check your CD's for errors? The option for that is in the first boot screen..

Is it common practice to have to check a CD I had just burned for errors? Or is it about the physical CD itself? And if it has something to do with the file being corrupt..where do you get one that isn't?




My apologies to all if I seem a bit snappy. It's a bit frustrating when you're willing to attempt to give it a try, and it's an uphill battle just to get it loaded on to the machine.

 I don't have the flexiblity to research how to get the OS to install and appear on my sceen like you might for a specific application or service to run. If you're installing an applciation, you can take your time and still use the rest of your computer until you figure out how to get it running properly. This is not the case when you have only one box and no OS. If I dont' have a working OS, I have no machine, and am dead in the water. This is not an option for me at the moment.

My thanks to all for your patience in advance.

---

### Post by stpieraf on 2007-03-21
Woops! Sorry guys.. It's not Dapper I've been working with, it's Edgy. So Edgey and Feisty!

My apologies for the confusion! :confused:

---

### Post by dracomordag on 2007-03-21
Ubuntu is a cliff, then a gradual slope. It was the same way for me.

all i can really suggest is partitioning off a little space (3-5 GB) from your old OS, installing through command line onto that partition, then trying it out. if you don't like it, wipe the partition.


command line install is easiest through the "Alternate LiveCD"

---

### Post by Bartender on 2007-03-21
there are 2 stages to md5 checks.  

First, you should download a windows-based md5 checker (I like md5Summer) and use it to verify the download.

The md5 sum you're looking for is right at the top of the blue list of files at the download site you used.  Scroll down the page a bit.  You have to run an md5 checker across your download, wait for it to generate the md5 checksum, then compare it to the number you retrieved from the download site.  Make sure to get the right md5 sum!  There are different ones for each download - i386, powerpc, amd64, etc.

The second step is checking the burned CD.  The first Ubuntu splash screen has an option to check the CD for errors.  If you can't even get there you might want to try the CD on another PC.

You probly oughta try the CD on another PC anyway.  If the LiveCD loads and gives you a desktop, then at least you know the CD's OK.

BTW, how fast did you burn the CD?  If you just tossed a CD in the tray and let your burn utility go at whatever speed it wanted to, that may be the prob.  Burn it at 2X or 4X.  I can get away with 8X on my P4 3 GHz.

---

### Post by dracomordag on 2007-03-21
> **stpieraf said:**
> 
Is it common practice to have to check a CD I had just burned for errors? Or is it about the physical CD itself? And if it has something to do with the file being corrupt..where do you get one that isn't?
you're right... its rare to check a DL'd file for corruption

on the other hand, how often do you DL an OS from of the internet?

---

### Post by stpieraf on 2007-03-21
> **dracomordag said:**
> Ubuntu is a cliff, then a gradual slope. It was the same way for me.

all i can really suggest is partitioning off a little space (3-5 GB) from your old OS, installing through command line onto that partition, then trying it out. if you don't like it, wipe the partition.


command line install is easiest through the "Alternate LiveCD"

That's fine suggestion, but unfortunately, I don't see it addressing the problem. I wouldn't MIND wiping the whole shebang if I knew at the end I'd have a computer that would boot up, but as it stands, I don't. The command line install sounds quite intimidating if you don't know what your doing, let alone dual booting and boot records, and wiping partitions, etc...

---

### Post by stpieraf on 2007-03-21
> **Bartender said:**
> there are 2 stages to md5 checks.  

First, you should download a windows-based md5 checker (I like md5Summer) and use it to verify the download.

The md5 sum you're looking for is right at the top of the blue list of files at the download site you used.  Scroll down the page a bit.  You have to run an md5 checker across your download, wait for it to generate the md5 checksum, then compare it to the number you retrieved from the download site.  Make sure to get the right md5 sum!  There are different ones for each download - i386, powerpc, amd64, etc.

The second step is checking the burned CD.  The first Ubuntu splash screen has an option to check the CD for errors.  If you can't even get there you might want to try the CD on another PC.

You probly oughta try the CD on another PC anyway.  If the LiveCD loads and gives you a desktop, then at least you know the CD's OK.

BTW, how fast did you burn the CD?  If you just tossed a CD in the tray and let your burn utility go at whatever speed it wanted to, that may be the prob.  Burn it at 2X or 4X.  I can get away with 8X on my P4 3 GHz.

I did try it at a fast burn speed. Although it doesn't make sense to me (and I'm probably wrong) that that would be the issue, I'll definitly give that a try. Thanks!


> **dracomordag said:**
> you're right... its rare to check a DL'd file for corruption

on the other hand, how often do you DL an OS from of the internet?

This is true. :)

---

### Post by dracomordag on 2007-03-21
wait, do you mean your old OS won't boot right now?

if its not broken right now, what makes you think that creating a new partition on your HD would change that? its common even when youre not switching OSes, i see no reason for your old OS to flip out

---

### Post by stpieraf on 2007-03-21
> **dracomordag said:**
> wait, do you mean your old OS won't boot right now?

if its not broken right now, what makes you think that creating a new partition on your HD would change that? its common even when youre not switching OSes, i see no reason for your old OS to flip out

No, it works fine now.

It's not the creation of the partion that concerns me. The boot records, which is the only way I can recall them, are managed by something (Loli or Lilo or whatever it was that used to manage them back in the day when I gave RedHat a shot, for example). So now, I'm changing that to make room for a Ubuntu boot.

What happens when I decide I don't want Ubuntu anymore? How do I fix the boot record? Will I be stuck eternally having to select windows from whatever boot manger that's used with a Unbuntu option that never works? How do you get rid of it?

There's a LOT of uncertainty there for someone who isn't that adept at this sort of thing. It's a lot of risk, with a high potential to lose everything I have or have to chang what I do every time I use the machine, for something that looks like it likely won't even work, and I may not even like in the end.

I thought that's what Live CD was supposed to allow me to do: Preview it without breaking anything. I don't want to install anything yet. I even went so far as to attempt to use MS Virtual PC (Something I've never used before, but seemed simple enough) to use the boot iso for Ubuntu, but I get processor and memory errors.


/Rant 

Is this as user friendly as Ubuntu can get? I don't want to be the jerk at the bar, but it's hard not to sound like him when every claim says this OS is easy and user friendly, and my machine won't even work with it. 

/End Rant

---

### Post by qamelian on 2007-03-21
> **stpieraf said:**
> I did try it at a fast burn speed. Although it doesn't make sense to me (and I'm probably wrong) that that would be the issue, I'll definitly give that a try. 

The faster you burn a CD, the less time the laser has to burn info to any given part of the disc. This results in a burn that is sometimes referred to as "shallow", which is harder to read than a disc that is burned at slower speeds. Any disc that you want to ensure can be read reliably, especially if it will be used in a drive other than the one used to burn it, should be burned at the slowest speed available (usually 4X these days).

---

### Post by stpieraf on 2007-03-21
> **qamelian said:**
> The faster you burn a CD, the less time the laser has to burn info to any given part of the disc. This results in a burn that is sometimes referred to as "shallow", which is harder to read than a disc that is burned at slower speeds. Any disc that you want to ensure can be read reliably, especially if it will be used in a drive other than the one used to burn it, should be burned at the slowest speed available (usually 4X these days).

Understood. Thanks for the tip, and the explaination! :)

I'll certainly give it a try.

---

### Post by Bartender on 2007-03-21
I read on this forum a few months back that you can actually burn too slow!  Something about the laser imparting too much energy into the pits and they start running together.  I don't know if that's true, but the guy sounded like he knew what he was talking about.
You've got a fairly modern processor and lots of RAM; you should be fine burning the CD somewhere between 2X and 8X.

I'm not familiar with AMD - is it a 64-bit CPU, and did you download the 64-bit version of Ubuntu?  From what I've picked up on this forum the 64 bit version is still kinda flakey...

Also, the alternate install CD (I think that's what was meant by the command line version) isn't hard to install at all.  It doesn't have a graphical interface like the LiveCD, and you can't take it out for a test drive.

But let's have you burn the CD slowly and see if that works first.

---

### Post by stpieraf on 2007-03-21
> **Bartender said:**
> I'm not familiar with AMD - is it a 64-bit CPU, and did you download the 64-bit version of Ubuntu?  From what I've picked up on this forum the 64 bit version is still kinda flakey...

Yes, I did. I also tried the i386 just for kicks. And it's unfortunate that it's flakey, since I don't think the i386 version will work at all if you have an AMD 64. (Could be wrong, of course, but I haven't had luck with either as of yet.)

> **Bartender said:**
> I
Also, the alternate install CD (I think that's what was meant by the command line version) isn't hard to install at all.  It doesn't have a graphical interface like the LiveCD, and you can't take it out for a test drive

.. That doesn't sound too appealing. :(

---

### Post by seshomaru samma on 2007-03-21
> **stpieraf said:**
> errors.


/Rant 

Is this as user friendly as Ubuntu can get? I don't want to be the jerk at the bar, but it's hard not to sound like him when every claim says this OS is easy and user friendly, and my machine won't even work with it. 

/End Rant

well, i dont know if you ever tried installing windows on a machine without preinstalled drivers - it could be a hellish nightmare. once you boot its ok  though...
if you buy a box with preinstalled linux you wont have this problem.

the command line install is not scary. for example windows xp's partitioner (on the installer disc) is also command line and most people can work it out. from reading your post you sound like a very intelligent person - i'm sure you will work it out.

the graphic installer has very limited grpahic option to make it fast , the OS itself is much more flexible and can deal with lots of hardware. 

please try dapper - its the most stable version of ubuntu.in the windows' world edgy would be beta and feisty alpha.

also - for a beginner - you shouldn't try the 64bit. the 32bit will give you much better results and is much easier to tweak

boot into windows -make sure you have an empty partition for ubuntu .remeber the partitions size cause linux names them differently.
you will install the boot menu ("grub") into the mbr . it will automatically recognise windows.
if you decide you dont like ubuntu just format it. you can recover windows' boot loader by running this command from an xp installation disk:
> fixmbr
(if you dont have an XP disk you can find many utilities that would do the same on the net)

---

### Post by sad_iq on 2007-03-21
Why not take a different approach and try to find out why the disc won't boot?
 Try the i386...as it works better...even on an AMD 64...and if burned at a low speed even better(assuming the md5 sums are correct!!)
 Boot with the cd..and when the **Start Ubuntu ** comes up press **F6**...a long list of text will appear ...find **splash** and **quiet** ..and delete them...then just press Enter...and (hopefuly) will see where the boot process hangs!!!

---

### Post by mcduck on 2007-03-21
> **stpieraf said:**
> Yes, I did. I also tried the i386 just for kicks. And it's unfortunate that it's flakey, since I don't think the i386 version will work at all if you have an AMD 64. (Could be wrong, of course, but I haven't had luck with either as of yet.)
64 bit CPU's run 32-bit operating systems just fine. Many people are actually using 32bit Ubuntu on 64bit platform as it some common software isn't available for 64bit Linux (like flash plugin, for example). It's possible to get them working in 64bit, but it takes some extra tricks to do that and many people don't consider running 64bit OS to be worth the trouble.

---

