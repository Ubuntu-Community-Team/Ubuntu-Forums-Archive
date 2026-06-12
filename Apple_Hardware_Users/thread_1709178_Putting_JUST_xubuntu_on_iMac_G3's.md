---
title: "Putting JUST xubuntu on iMac G3's"
date: 2011-03-17
forum: Apple Hardware Users
---

### Post by Airamith on 2011-03-17
Ok, so I have eight iMac G3's that work. I've never had a mac before, and I'm not interested in anything the mac OS has to offer. I want to totally delete it, and put JUST xubuntu on these computers. I know nothing about Mac, except I got these, and they have pretty colored housings. I've tried using the 'c' and 'apple+c' commands to get this to boot from the xubuntu cd, but it doesn't have any effect. The thing just continues to load OS9. 

I'm seeing from all these threads that everyone is pretty much dual booting, or multi-partitioning the hdd. I do NOT want to do this. Is it possible to format the drive completely, so that it is utterly blank, and then install xubuntu? Am I going to have to get new hdd's for them? They all work just fine, no problems except the software is so old that you can't do anything with it but use post it notes. 

Advice please!

---

### Post by snafu006 on 2011-03-18
did you download the Powerpc version of it and i world download ubuntu 10.04 ppc and then you can add the xubuntu after ubuntu is installed are thos imac slot loading or tray?

Step one down load ubuntu 10.04 ppc (powerpc) and burn to cd 

Step two start computer computer and hold option wait from a screen to come up then put cd in ok.
 
Step three follow this on second page are picturs i posted it will help you a lot. [http://ubuntuforums.org/showthread.php?t=1689694](http://ubuntuforums.org/showthread.php?t=1689694)

---

### Post by Rustman80 on 2011-03-18
Disregard.  They did make the alt installer under 700mb for 10.10.  I wasn't able to find it yesterday.  I was quite annoyed with the previous ISOs all being 705mb to 725mb.

---

### Post by Airamith on 2011-03-18
They're slot loading, and they have all original hardware. Obviously when I get some extra cash I'm going to put more ram in them (I just found out I can do that) but other than that they're going to stay the same. I was told to use xubuntu because it's...smaller? I don't know really, I was just told that they may have an easier time running xubuntu instead of ubuntu. They only have 10gb hdds, will this make a difference?

---

### Post by Rustman80 on 2011-03-18
Ok... issues that I've found with the G3's so far.  I have 30 of the G3's that you are working with and have pretty much been fighting with them for the last 3 weeks, so here are my lessons learned.  I was installing regular Ubuntu on them, so things might be different a little, but I doubt it.  I'm putting Xubuntu on right now, so when its done installing I'll post what I find.  

First, Xorg doesn't work on install, so your desktop won't function.  The first time you boot after install, when it asks for boot options, you'll want to boot with "Linux video=ofonly".  This will get you to the command prompt on boot.  From there you'll have to build the xorg.conf file from scratch to make it work with the iMac G3.  I have a file saved that works for me, so if you want it, let me know.  While you are in command prompt, I'd get rid of TTY 3 through 6, and modify the sysctl.conf file to lower the swappiness to 10.  Both seem to marginally improve the performance of ubuntu on the G3 (still not great, but functional).  The last problem I'm having is that Ubuntu misidentifies the CD-ROM device as hdb instead of cdrom, making the slot cdrom non-functional in the desktop without manually mounting it via the terminal, which is really really annoying.

UPDATE:  I found that Xubuntu does not have a "My Computer" section with a default CD-ROM device like regular Ubuntu has.  As a result it actually recognizes CD's correctly and automatically mounts them to the desktop when inserted.  One less thing I have to bother with.

---

### Post by Airamith on 2011-03-19
That is beautiful news. Now, will that  xorg.conf file you use for ubuntu, will it work for xubuntu? I'm not too worried about the cd-drive after I get the OS installed. The four I'm working on right now are going to be limited access use for kids. They don't really need a cd-rom.

---

### Post by snafu006 on 2011-03-19
> **Airamith said:**
> That is beautiful news. Now, will that  xorg.conf file you use for ubuntu, will it work for xubuntu? I'm not too worried about the cd-drive after I get the OS installed. The four I'm working on right now are going to be limited access use for kids. They don't really need a cd-rom.

So to get the right xorg.conf file I need to know you computer clock speed find terminal and type or past      *cat /proc/cpuinfo* This will give you a reading like this
 > snafu@Linksys:~$ cat /proc/cpuinfo
processor    : 0
cpu        : 750CXe
temperature     : 26-28 C (uncalibrated)
clock        : 600.000000MHz
revision    : 34.21 (pvr 0008 2215)
bogomips    : 49.92
timebase    : 24960000
platform    : PowerMac
model        : PowerMac4,1
machine        : PowerMac4,1
motherboard    : PowerMac4,1 MacRISC2 MacRISC Power Macintosh
detected as    : 256 (iMac "Flower Power")
pmac flags    : 00000010
L2 cache    : 256K unified
pmac-generation    : NewWorld
Memory        : 1024 MB
 Now why i want to know this is because the old iMac g3 have differnt Video cards and if you dont have the right xorg.conf file then the computer will not work right. See my Imac has Ati Rage 128 Pro Ultra TR your imac can or will not be the same please post your *cat /proc/cpuinfo*

> snafu@Linksys:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea AGP
0000:00:10.0 Display controller: ATI Technologies Inc Rage 128 Pro Ultra TR
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Pangea Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth/Pangea FireWire
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth/Pangea GMAC (Sun GEM) (rev ff)


---

### Post by sword_king on 2011-05-08
Airamith,

I came across one of your posts on another thread, and found my way here. After having messed with imacs and emacs for quite a few years, I have come to the conclusion that it is a good thing to have a small os9 partition if only for one reason. These monitors don't have any 'hardware' controls, where you can push some buttons on the monitor and adjust the display left/right, up/down, rotate, etc. My imacs all tend to get a little distorted, small and tilted (rotated) when I clear the PRAM, which I seem to need to do quite often (once a month or even every other week cuz I keep trying out different stuff). The only way to adjust the monitor is thru the MacOS, in Preferences on OSX or with the Monitor Control Panel in OS9. You can get an OS9 installation (with everything you need) in a <500mb partition, leaving the rest of the disk for *ubuntu, Debian, MintPPC or whatever. Even an old 233mhz tray-loading imac will run well with Debian if you max out the RAM.

If you can get Dapper or Edgy running, you can also use MOL (Mac-On-Linux) which will allow you to use the programs (iTunes comes to mind) on your Mac side from within Linux, like Classic from within OSX.  You would probably want a bigger OS9 partition if you did that, tho'. Fun and Games!!

Good Luck with your project. BTW, to get any real help, post the specs of the machines. Better yet, a link to the description on <everymac.com>

HTH, SK

---

### Post by sword_king on 2011-05-10
I got to thinking about what I wrote a couple days ago, and realized I have an extra 512mb USB flash drive laying around, so I stuck it in my g3 600mhz imac and installed a fairly minimal OS9 on it. It used less than 135mb and boots into OS9 just fine by holding the <option> key while booting. The monitor can be set from there and so you wouldn't need a dedicated OS9 partition on each computer.

I've tried it on 2 iMacs and it worked the same way on both. YMMV

However, if I were doing what you're doing, I would probably go the MintPPC route <mintppc.org> 

HTH, SK

---

### Post by Kurlon on 2011-05-12
I use xvidtune to tweak the display on my 1st gen slot load iMac G3 from within Ubuntu.  It is limited to horizontal/vertical stretch and placement but so far that's all my machine has needed.

Now if I can just sort why X breaks completely with 11.04 I'll be happy...

---

