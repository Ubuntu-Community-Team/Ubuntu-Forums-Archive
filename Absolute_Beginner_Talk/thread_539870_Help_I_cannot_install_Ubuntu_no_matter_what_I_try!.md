---
title: "Help I cannot install Ubuntu no matter what I try!!!!!"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Azerial on 2007-08-31
PROBLEM SOLVED!
I burned the ISO of 7.04 Live CD, to a CD Rom instead of a DVD using Img Burn, burning at a 1x speed.
Installed flawlessly





(note this was copy pasted from the installation & upgrades forum due to lack of timely replys there where as my posts here tend to get a lot faster response and I am a linux newb so I guess it qualifies to go here too)

I am becoming BEYOND aggravated (to put it nicely and without language some many consider offensive) Trying to Install ubuntu 7.04 or 6.06 on my system.

For Reference Heres the specs as listed by New egg where I bought the parts from

BIOSTAR TF560 A2+ AM2+/AM2 NVIDIA nForce 560 MCP ATX AMD Motherboard

AMD Athlon 64 X2 5200+ Windsor 2.6GHz 2 x 1MB L2 Cache Socket AM2 Processor

G.SKILL 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory

EVGA 256-P2-N615-TX GeForce 7600GT 256MB 128-bit GDDR3 PCI Express x16 SLI Supported Video Card

Seagate Barracuda 7200.10 ST3320620AS (Perpendicular Recording Technology) 320GB 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drive

LITE-ON Black 20X DVD+R 8X DVD+RW 8X DVD+R DL 20X DVD-R 6X DVD-RW 12X DVD-RAM 16X DVD-ROM 48X CD-R 32X CD-RW 48X CD-ROM 2MB Cache SATA DVD Burner

(and if it matters which im 99.99% sure it wouldnt my case)
RAIDMAX SMILODON ATX-612WBP Black SECC STEEL ATX Mid Tower Computer Case 500W Power Supply



Ubuntu 6.06

Result, some kinda kernal panic and something about Apic
-pressed F6 on recommendation of a user in the forums and set it to noapic and pressed enter, Instilation gave errors and froze up.

-pressed F6 and typed apic=off, same problem errors and froze up

Downloaded 7.04 and burned the Iso to a DVD
Install went normal until it kept popping up something about
"Buffer I/O error Fd0" or something like that filling my screen, the screen went black and froze up nothing happened for fifteen minutes I assumed frozen and restarted.

Downloaded 7.04 alternate tried the text installer

Everything went fine until it asked for CD Drivers. I dont have a floppy disk with drivers for my cd drive, its SATA, Lite ON DVD Burner, CD burner Combo drive. I didnt have drivers on my disk anywhere, I tried to skip that it wouldnt let me, or in other attempts it let me and the screen went all funky and I couldnt read anything.

Also 7.04 Live CD would not install in safe graphics mode either, gave SAME issue with I/O error

Is Ubuntu's installer a piece of crap that hates up to date hardware?

Can I get around these problems and get this damn thing installed

Or am I gonna have to get another Distro of Linux?

If I have to get another distro of linux please give recommendations, I liked What I saw in Ubuntu, so please the more like Ubuntu the better.

---

### Post by Roaster on 2007-08-31
Try to burn the disk at a lower speed. Sometimes if you burn an image at the fastest burn speed you will get write errors. Try a write speed of 4. I know it sounds crazy but I have had it happen to me. Stick with Ubuntu you'll love it.

---

### Post by Sef on 2007-08-31
1) Did you md5sum the download?  (Verifies the download is good.)

2) Did you burn the iso at 4x or less? (Higher speeds can cause a bad burn.)

3) Did you check the disk for errors?

---

### Post by HermanAB on 2007-08-31
Hmm, either a bad disk as suggested, or you got to try a different distribution.  If you get more than one or two issues during an install, then it is better to try another system such as Mandriva, Fedora, Suse, Mepis or whatnot, rather than banging your head against a wall.  

The reason being that each distribution has a different install wizard and some can figure things out that others can't - it depends on what the people had available when they developed their installers.  While the big distro's have big labs, they don't have one of everything ever produced in the world...

Cheers,

Herman

---

### Post by Azerial on 2007-08-31
> **Sef said:**
> 1) Did you md5sum the download?  (Verifies the download is good.)

2) Did you burn the iso at 4x or less? (Higher speeds can cause a bad burn.)

3) Did you check the disk for errors?

that first thing md5sum is greek to me mate, care to elaborate?

---

### Post by Siph0n on 2007-08-31
I have had problems installing ubuntu on my new laptop because there was not an unallocated space for it. The laptop came with Vista, so I had to go into Vista and create a new partition for ubuntu... Dunno if this helps any, but good luck :)

Siph0n

---

### Post by p_quarles on 2007-08-31
> **Azerial said:**
> that first thing md5sum is greek to me mate, care to elaborate?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Azerial on 2007-08-31
> **Siph0n said:**
> I have had problems installing ubuntu on my new laptop because there was not an unallocated space for it. The laptop came with Vista, so I had to go into Vista and create a new partition for ubuntu... Dunno if this helps any, but good luck :)

Siph0n

Way ahead of ya there buddy when I installed XP Pro on this system I made 2 partions roughly a tad over 150gb in size out of my 320gb harddrive

---

### Post by Azerial on 2007-08-31
> **p_quarles said:**
> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

my alternate version hash checked out just fine

---

### Post by chamberlain2006 on 2007-08-31
I noticed you had an APIC error.  Perhaps try adding noapic to the boot parameters (Press F6 (i think) when the cd starts and type in noapic at the end)

---

### Post by Azerial on 2007-08-31
> **chamberlain2006 said:**
> I noticed you had an APIC error.  Perhaps try adding noapic to the boot parameters (Press F6 (i think) when the cd starts and type in noapic at the end)
already tried that, no luck

---

### Post by Chilongola on 2007-08-31
Your problem is for sure the cd.  Re-burn at 4x as suggested.  Or re-download without a pause.

---

### Post by Kevin the Olden on 2007-08-31
Start pulling RAM chips or using some from another PC. Pull everything not needed like above board LAN, wireless, video cards etc. Try an install to a minimum system. See what happens.

---

### Post by Azerial on 2007-09-01
Problem Solved.

I have NO idea why this worked

The CD my friend gave me thats an offical Live Distro CD a friend ordered did not work.
the Live DVD of 7.04 I burned, no work
the DVD of 7.04 alternate I burned no work

I burn a CD of 7.04 at 1x speeds, Works FLAWLESSLY  SO WOOT I got Ubuntu

---

### Post by Chilongola on 2007-09-01
Yep it usualy is a bad burn.  Glad to see you made it!!

---

### Post by Lord Illidan on 2007-09-01
I was going to suggest changing your mousemat..

---

### Post by Azerial on 2007-09-01
> **Lord Illidan said:**
> I was going to suggest changing your mousemat..

wtf is a mousemat?

and by the way I now have another ISSUE with Linux, its not recognizing my SATA CD/DVD burner combo drive

[http://ubuntuforums.org/showthread.php?t=540008](http://ubuntuforums.org/showthread.php?t=540008)

---

