---
title: "Linux For a Old PC"
date: 2013-05-09
forum: Any Other OS
---

### Post by IWantToBelive on 2013-05-09
I have a old computer...
150 MHz CPU / 192 MB RAM / 2 MB / 20 GB HDD
I installed windows 98, and it works fine.... but I like a Linux on that machine...
I tried [Slitaz]("http://www.slitaz.org/en/") but I can't play mp-3 in it... :(

All I want it to do are "play music, view PDFs" (and view basic web, get mail if possible) (and should look cool :))
Any ideas?

---

### Post by slickymaster on 2013-05-09
Give [Bodhi Linux]("http://www.bodhilinux.com/") a try.

---

### Post by Cheesemill on 2013-05-09
[CrunchBang]("http://crunchbang.org/")

---

### Post by tgalati4 on 2013-05-09
*[tinycore]("http://tinycorelinux.net/screenshots.html")* linux might do it.   You are pushing the limits for anything resembling a modern desktop.

---

### Post by Lars Noodén on 2013-05-09
In addition to tinycore, there is also [puppy](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

### Post by smellyman on 2013-05-09
> **Lars Noodén said:**
> In addition to tinycore, there is also [puppy]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

Specifically Wary Puppy....

---

### Post by snowpine on 2013-05-09
To play mp3 in Slitaz see here: [http://doc.slitaz.org/en:handbook:multimedia](http://doc.slitaz.org/en:handbook:multimedia)

As soon as you have a few $$ I recommend to upgrade your hardware. Raspberry Pi has better hardware specs and costs $35. iPhone has better hardware specs and is free with 2 year activation. ;)

---

### Post by Rukiri on 2013-05-09
Without knowing what your CPU is it's hard to say, was this a custom PC build from back in the day or was it purchased from a vendor like HP, Dell, Gateway2000(gateway now), compaq, etc?

Please list the model number, your best bet is source based as you can compile it specifically for your architecture, but if that's not your thing you can probably go with Arch Linux and a Xfce4 setup (depending on your gfx card you may be able to use compisiting). 

This may be a one case scenario where you actually have to build linux from the ground up, I've done with with very old 1993 and 1995 machines even IBM PCs from the 80s due to the fact the architecture is ancient, but the 90s is old but would not call it ancient just yet as pentiums and old amd chips are still in use but there usage as a desktop pc is well limited unless they were using something built during that time like windows 95 or windows 3.1.

If you think windows 98 runs great you should be able to install xubuntu just fine, I'd go on a lim and say go source based for an optimal experience (you should get the same performance as windows 98 if not a little better)  Now obviously you may be a tad limited in what you can actually do here, but if all you want is to view pdfs play music I'd probably just go with Lubuntu or Xubuntu or even Linux Mint with an ext2 filesystem.

Since it's more likely a windows 98 machine there is a few things I'd do and it's beyond cheap, believe it or not there are some manufactors that actually still produce ram in the MB, I'm fairly certain it's either sdram or ddr ram so please list the computer with the model number.

I'd upgrade the ram to probably 256MB, if possible go 512MB (most Win98 PCs were able to be upgraded to 512MB and 1GB was probably the max at that time and kinda was until WinXP (when I used WinXP my parents PC still only had 512MB as it was still the standard as of 2001- to I'd say 2005/6 when 4GB became the norm).  I'd also update the soundcard as you want to listen to music (and if your like me) to the best quality possible for your machine, it should have PCI express 1X so look for a soundcard for PCI 1X.

I'd also update the gfx card if it's not to your liking.

And for your partitioning.

Boot - 200MB
Swap - 384MB (because of the 1GB rule, google linux swap)
Root - Rest of the disk (I generally don't create partitions for /var /usr /home, as I personally see no reason to mainly due to the fact that when you install a package through a package manager it's often installed on /root so if I limit root and run out I"m screwed...  

You should probably have 18GB of free storage due to the fact the filesystem reserves disk space.

Here are my choices on a pure guess of your hardware.

Debian Stable (7.0 MAY work, still go for xfce or even openbox)

Gentoo/Funtoo (For optimal performance but it does take awhile to get up in running (takes maybe a day to get vlc, firefox, and kde compiled for my system but that includes me leaving for a few hrs when the compile probably took 30 minutes as I generally watch a lot of movies (my dvr atm is jam packed full)

Xubuntu if you want to stay with the ubuntu ecosystem but use xfce by default, nothing wrong with that.

Linux Mint Debian with XFCE4 (debian testing + mint) basically this will have what you want out of box

OpenSuse 12,3 + xfce4 (use the Suse Studio to build your 12.3 system with the applications you want, I'd probably go with shotwell, vlc, any pdf app will work, libreoffice, and various codecs, you will probably have to use an old driver if your using ati or nvidia, you may have a 3dvoodoo card if it's as old as I think it is.)

Linux From Scratch (build your system yourself, I will not lie it takes 12 days and a week to do anything, I'd stick with the gentoo rout)

SourceMage (same reason as Gentoo but the install media is old by 2 years so it has no modern features by default (it's as up to date as gentoo but you can't use btrfs by default) but for your system it should be fine and I find sourcerer easier to manage than portage plus it's graphical for the options you want in your applications)


For me I'd always go source but you may want to be running your system now instead of next week in that case Mint, Xubuntu, or Debian would be your best choice.

This may be the one time I recommend staying with windows due to age, the software will be old there's no doubt about that but Linux to me wasn't usable until kernel 2.8 (or was it 3.0?) It's recently just got better and fast.

---

### Post by Sam Mills on 2013-05-09
> **tgalati4 said:**
> *[tinycore]("http://tinycorelinux.net/screenshots.html")* linux might do it.   You are pushing the limits for anything resembling a modern desktop.
I agree with this. You would be lucky to get any semi-modern linux to install. Perhaps an old version of linux from the early 2000's will work, but even then probably not very well.

---

### Post by Rukiri on 2013-05-10
He's well in line with Arch Linux, I'm actually moving over to Arch Linux from Gentoo (I can't be bothered to compile everything from source, I will still compile the kernel from source, and my desktop environment (kde is kinda buggy on arch, apps just load slow or something, runs quick and smooth on gentoo (using it now)).

Here is the recommended system requirements for Arch. 

i686 or x86_64 architecture
128MB of ram (I'd seriously upgrade your ram to your max, it'd probably cost under $50)
2GB HDD space

The gfx requirements are up to you but openbox, lxde, and xfce4 should fit you nicely.

You may have to do a lot of compiling due to your ancient hardware but for music and pdfs I think you can work with arch.

---

### Post by mörgæs on 2013-05-10
Send it to recycling. 4-5 years old hardware is so cheap that it's not worth the effort.

---

### Post by Rukiri on 2013-05-10
OLD PCs/Macs still have use today, just not as much as when you originally bought them.
Most are used as file servers.

---

### Post by mörgæs on 2013-05-10
Yes, a headless server is an option, but I would not recommend anything with a GUI on a 150 MHz processor. Am I right guessing something like 16 years of age?

---

### Post by mörgæs on 2013-05-10
> **Sam Mills said:**
> I agree with this. You would be lucky to get any semi-modern linux to install. Perhaps an old version of linux from the early 2000's will work, but even then probably not very well.

An old (=unsupported) distro is a security breach.

---

### Post by Rukiri on 2013-05-10
A Gui desktop is perfectly possible however... he will have to compile from source, I recommend arch but gentoo may be easier to manage due to the fact it's probably a 486 but could be a 586 cpu, he hasn't responded with what he really has he just gave us I have a 150MHZ cpu, 20GB of hdd, and 192mb ram.  Sums up it's from 1997-1998.   There's no way he's getting kde to rythambox or banshee will work fine under a 386, 486, and 586 just fine but the key is compile it for that architecture plus it will use less resources.

I recommend openbox as it at least gives you a right click menu and it's easy to use.

A Nice install for 586 for arch, still works today.
[https://wiki.archlinux.org/index.php/Install_Arch_i586](https://wiki.archlinux.org/index.php/Install_Arch_i586)

Again for pdfs and music, and ancient hardware just use windows 95 or even 98 and call it a day.  Linux is awesome but it's constantly moving, I'd probably go as far as saying use windows 3.1, I know you want linux but there's no getting around compiling everything due to your ancient hardware.

---

### Post by excollier on 2013-05-10
Again, Puppy would do well on that.

---

### Post by kiyop on 2013-05-11
I guess that the CPU is i586 or later because clock rate of i486 is under 100MHz according to [https://en.wikipedia.org/wiki/Intel_486](https://en.wikipedia.org/wiki/Intel_486), although I am not sure.
[https://en.wikipedia.org/wiki/80586](https://en.wikipedia.org/wiki/80586)

I suggest debian without broat desktop environment with OpenBox.
I have a laptop PC; IBM thinkpad X22 with 128MB RAM and I enjoy surfing the web with debian sid and iceweasel on it.
(It has PentiumIII-M 733MHz, which is by far faster than the CPU of the OP's PC.)

---

### Post by IWantToBelive on 2013-05-11
Thank you everyone for your response
Sorry I didn't wrote this data at first...

Processors Information
-------------------------------------------------------------------------

Processor 1                     ID = 0
        Number of cores         1 (max 1)
        Number of threads       1 (max 1)
        Name                    Intel Pentium
        Codename                P54
        Specification
        Package                 Socket 5 (296)
        CPUID                   5.2.C
        Extended CPUID          5.2
        Core Stepping           cC0
        Technology              0.35 um
        Core Speed              149.8 MHz
        Instructions sets
        L1 Data cache           8 KBytes, 2-way set associative, 32-byte line size
        L1 Instruction cache    8 KBytes, 2-way set associative, 32-byte line size
        FID/VID Control         no

Chipset
-------------------------------------------------------------------------

Northbridge                     Intel i430TX rev. 01
Southbridge                     Intel 82371AB (PIIX4) rev. 01
On Board Cache                  512 KBytes
Memory Type                     EDO
Memory Size                     128 MBytes


Memory SPD
-------------------------------------------------------------------------

DIMM #                          1
        SMBus address           0x51
        Memory type             SDRAM
        Manufacturer (ID)        (0000000000000000)
        Size                    128 MBytes
        Max bandwidth           PC133 (133 MHz)
        Part number
        Manufacturing date      Week 99/Year 37
        Number of banks         2
        Data width              64 bits
        Correction              None
        Registered              no
        Buffered                no
        EPP                     no
        XMP                     no
        AMP                     no
        JEDEC timings table             CL-tRCD-tRP-tRAS-tRC @ frequency
        JEDEC #1                2.0-2-2-5-n.a. @ 100 MHz
        JEDEC #2                3.0-3-3-6-n.a. @ 133 MHz

This is a custom built computer.
It has 4 SIMM modules but when DIMM is installed CPU-Z doesn't detect (SIMMs  are 16 MB each)

This is the link to the [full report]("http://goo.gl/YTMBO") if you need it
This is the link to the [Main-board manual]("http://www.motherboards.org/files/manuals/1/txp4-200.pdf")

Yes I know this is too old.. :(
But I'd really like to use it...

---

### Post by ronniew on 2013-05-11
LXLE may do the trick for you. Should run with those specs. Its like the shelby version of Lubuntu 12.04 , its at 12.04 to ensure support for older hardware.

[www.lxle.net](www.lxle.net)

---

### Post by snowpine on 2013-05-11
AntiX is nice for really old computers :)

---

### Post by Plumtreed on 2013-05-13
Suggest you have another look at Slitaz, I'm sure it is possible to run MP3. I have tried many different OSs but found Slitaz offered a decent speed and a great selection of practical applications to adopt if needed.........my old PC has a bit more ram than yours and I still use it with Slitaz....even tho it came with Win98!

---

### Post by aezakmi on 2013-05-15
If you are searching for a good distro take a look on [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by IWantToBelive on 2013-05-22
I tried Puppy, but it was too slow... :(
Can anyone tell me something lighter than Puppy...
[I know, the best thing to do is change the computer... :)]

---

### Post by mips on 2013-05-22
[http://en.wikipedia.org/wiki/Tiny_Core_Linux](http://en.wikipedia.org/wiki/Tiny_Core_Linux)
[http://en.wikipedia.org/wiki/SliTaz](http://en.wikipedia.org/wiki/SliTaz)
[http://en.wikipedia.org/wiki/BasicLinux](http://en.wikipedia.org/wiki/BasicLinux)
[http://en.wikipedia.org/wiki/Damn_Small_Linux](http://en.wikipedia.org/wiki/Damn_Small_Linux)

Try those.

---

### Post by lykwydchykyn on 2013-05-22
I honestly don't think you're going to get an enjoyable linux experience on that hardware no matter what you choose.  There are a few other OS options out there, here's a blog post I did exploring some of them:

[http://www.alandmoore.com/blog/2012/12/14/replacing-windows-98-and-other-seemingly-impossible-tasks/](http://www.alandmoore.com/blog/2012/12/14/replacing-windows-98-and-other-seemingly-impossible-tasks/)

---

