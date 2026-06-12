---
title: "Intall Problem ::Pic of problem inside::"
date: 2005-09-26
forum: Absolute Beginner Talk
---

### Post by quattroman on 2005-09-26
[http://dubs.unixprohost.com/albums/album69/DSC06262.sized.jpg](http://dubs.unixprohost.com/albums/album69/DSC06262.sized.jpg)

can anyone help me? I am a new , completely new at Linux.

---

### Post by PsyberOneZero on 2005-09-26
did you compile the kernel yourself or is that a standard (ubuntu) kernel.

If the second, Which release (warty, hoary or breezy) and which kernel (2.6.x-x)

---

### Post by quattroman on 2005-09-26
I am sorry....I am so lost is not funny anymore....
I send my CD to boot, press install and I get that...

in adition its, P3 877, 512 ram.

Can I start from the basics? What is Kernel? What is compiling?

---

### Post by quattroman on 2005-09-27
a friend of mine told me that on the line 
[4294673-029000] RAMDISK: Incomplete Write .......
and the following "crc error" are cd errors, 
re-burning the cd at low speed will it help? The first one was made at 40x (top speed)

---

### Post by PsyberOneZero on 2005-09-27
That is always a good idea with install cd's.

I wasn't trying to confuse you I was just trying to narrow down the possible error but that is most likely the problem.

---

### Post by dguitar on 2005-09-27
I had a similar error on an old P1. Burned it at 4x and worked like a charm.

---

### Post by quattroman on 2005-09-28
I re burned the cd (this time HOARY), i got the same problem. I am gonna get a pic of it later, It seems to have more detail.

I need someone to explain to me, what is kernell? compile? and how do I compile kernell?

thanks

---

### Post by Kyral on 2005-09-28
Kernel == Heart of the OS, any OS. Be it Windows, OSX, Linux, Amiga, DOS, whatever. Its the "lowest level" software in the system. Coordinates actions between software and hardware (there are a few exceptions).

Example: You tell Word to save a file to disk. What you see is that it is saved. What really happens is that Word asks the kernel to put that data on the hard disk. There is more to that, but thats the basic idea.

Compile means to turn computer langauge (C, C++, Java, etc) into machine code.

So if you don't know what those terms mean, I wouldn't compile your own kernel :P I'm a Linux Vet and I avoid doing it if I can.

So Kernel Panic you can guess is one of those few errors that can cripple a system completely. The good thing is that if you boot, you won't get it as long as you are booted :P

I would reccommend looking up those terms in the WikiPedia for much more info

---

### Post by quattroman on 2005-09-28
now I got the basics....
but I never studied/learned any language, it is on my to-do list. I gonna go for C C++. 
But on the mean time, can anyone give me the steps to configure that and install the OS? 

I am greatly appretiating all the help.

---

### Post by az on 2005-09-28
[QUOTE=quattroman]I re burned the cd (this time HOARY), i got the same problem. I am gonna get a pic of it later, It seems to have more detail.

I need someone to explain to me, what is kernell? compile? and how do I compile kernell?

thanks[/QUOTE]
The problem seems to be that your hard drive cannot be found.

Please post the pic of the Hoary attempt.  That would be helpful.  This is probably a bug.

---

### Post by d1337 on 2005-09-28
A little more machine history may be helpful as well.  Are you hoping to overwrite an existing OS (win?) and if so, is it working correctly.  Going with Azz, if it can't detect your hd, I'd check connections and setup.  Is the hd on primary ide? is it set as master, slave or cable select?  Are these connections tight and clean.  I've headached over many attempts at building a box from scrap/leftovers only to find that a little time taken to clean it out and tighten it up does the trick...but that's just my 2 cents.

d1337

---

### Post by quattroman on 2005-09-28
Computer INFO, as requested:

P3 877
512 Ram (on 2 128 + 1 256)
ASUS mainboard CUSL2 ACP1 BIOS
3 HDs: 1) 10GB MASTER (WIN XP) IDE1
          2) 10GB CABLE SELECT (Place for UBUNTU) IDE1
          3) 40GB SLAVE (NAS+FTP) IDE2
Wireless conection on a D-LINK B PCI card
USB Mouse
PS/2 Keyboard
CD-ROM (burning of CDS is done in a newer computer) IDE2

I think that is it.
Right now I am going to get the error and take a picture.

---

### Post by quattroman on 2005-09-28
Pictures....
[Actual Computer and Location](http://dubs.unixprohost.com/albums/album69/DSC06276.sized.jpg)
[main board model at boot](http://dubs.unixprohost.com/albums/album69/DSC06279.sized.jpg)
[Ubuntu hoary error](http://dubs.unixprohost.com/albums/album69/DSC06278.sized.jpg)

---

### Post by az on 2005-09-28
Try running memtest from the Breezy install cd.

The Hoary error message says that the ramdisk is bad.
Hmmm.

---

### Post by quattroman on 2005-09-28
how do I do memtest?

RAMDISK? Meaning?

---

### Post by d1337 on 2005-09-28
I believe that you can just type memtest at prompt from the installer disk, as opposed to just hitting enter.  Memtest will ensure that your ram is working/not corrupt/not causing issues.  Let it make a couple of passes...probably take 30-45minutes/pass for your 512mb on that machine.
I noticed that in the second pic, bios is installing plug and play.  Is there an option in bios to allow the operating system to handle that.  IIRC, Linux isn't nuts about plug and play.
Just out of curiosity, have you tried an install with your box turned in its native mini-tower position as opposed to horizontal.  Your cd rom may read a bit easier.  I had a box that refused to read a cd if it wasn't sitting properly...but that could've been the burn just as well.
d1337

---

### Post by az on 2005-09-28
Google memtes86.

Download the thing and write it to a floppy (there is detailed documentation on how to do this on the site)  Boot your computer witht that floppy (tell your bios to boot from the floppy) and run the memory test.

When you start linux, it loads stuff into a virtual filesystem it creates in memory (a ramdisk)  If you have bad memory, your system crashes.  Could this memory be bad?  Was the computer recently running fine?

---

### Post by quattroman on 2005-09-28
On XP the computer runs very smoothly, I got an FTP server running all day, very fast...but the MEM sticks are old.

I don't own a floppy drive.

---

### Post by quattroman on 2005-09-28
[http://www.memtest86.com/#download0](http://www.memtest86.com/#download0)         should I download this?

---

### Post by az on 2005-09-28
Yeah, you should then use the iso images and make a cd. 

But if you are already running an OS on it, that probably is not your problem?  I dunno.  Did you try booting with some of the boot arguments found in the F3 F4 F5... menus?

Also, what are the drive types in BIOS?

(FTP on XP?  Yeesh!)

---

### Post by quattroman on 2005-09-28
FTP on XP.....yes, but I want to try linux to host, in future my own website and ftp, plus others I might come up with
where do I check the BIOS Drivers? (BIOS SETUP?)

---

### Post by quattroman on 2005-09-28
NERO burning ROM (6 Ultra) does not support that ISO file...what other way do i have to burn it

---

### Post by d1337 on 2005-09-28
While you are looking in bios, what is PNP (plug & play) set to?

---

### Post by quattroman on 2005-09-28
Plug & Play O/S    [NO]  available options YES or NO

can't find BIOS version, but isn't the one in the picture named Mainboard model?

---

### Post by quattroman on 2005-09-29
de ISO from memtest86 is not good, at least for me, so I cant run that operation by CD boot, and I dont own FLOPPYs (Now I regret that)

---

### Post by quattroman on 2005-09-29
after reading some info on memory errors, I decided to read the error and see what I could understand, and I found an address error, so a memory stick is bad, I gotta figure out which of the three it is and try to run install again.

I will keep you guys posted, if anyone cares.

---

### Post by quattroman on 2005-09-30
Reviving my thread, 
I finally got memtest and found one of my mem stix to be dead, so I went again at install, and finally was able to.
But got to cancel, my spare HDD that I salvaged from a destined to trash PC was also bad, so I need to part the XP HDD, but thats when I have more time.

In the mean time, which of all partition formats do I select? there are like 10 options?


Thanks for all previews help and for keep bearing with me.

---

