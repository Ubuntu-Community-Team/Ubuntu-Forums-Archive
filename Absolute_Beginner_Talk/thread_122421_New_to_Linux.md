---
title: "New to Linux"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Nitrous570 on 2006-01-27
Hello all, I am new and know almost nothing about linux in general. My friend said that he likes the stability of unbutu, and the speed of it too. It has interested me into finding out more about unbutu, whether I could switch or not. 

My System:
AMD Athlon 64 x2 4400+ dual core processor
Asus A8N-E motherboard
And a x800xl 512mb saphire radeon card. 


Basically, I needed to do a lot of work to configure and install windows. I needed to downgrade the BIOS, install windows, upgrade the BIOS, and then finally, get the drivers for my video card. Now, the thing that I am having concerns about, is that it is dual core. I had to go the the amd site and download a patch so that my processor could communicate better with direct x9, and stuff. Finally, after downgrading the BIOS, uprgrading it, downloading and installing my video card drivers, and that patch, was I able to go. 

My problems are:
1) will ubuntu, 5.1.0 or whatever it is work on my system. 
2) my board is a pci-e i think (not sure; ne one know?)
3) will i have to downgrade the BIOS? then updrade it again? 
4) Can i run windows apps on ubutu though something like code weaver?
5) will i be able to play games on my comp? (cedega?)
6) can i get drivers for my x800xl 512mb video card if i am running windows? are they the same as the windows drivers??


I am really hoping that I can run ubuntu linux, windows is driving me crazy. So unstable, and and ridiculously slow,even with my system. Plz help . thx. :)


And will unbuntu recognize all my hardware. I have:
- Asus A8N-E socket 939 nforce 4 w/audio, sata
-logitech x230 - 2.1 surround sound speakers
-BENQ P010-u51b keyboard
-Logitech MX510(red) high performance optical mouse
-DVD-RW - OEM BENQ DW1640 dvd rewritable drive
- 3 gigs kingston ddr pc 3200 ram
- and at last the amd athlon x2 4400+ dual core processor*

*that is the one that I am most worried about, along witht the pci mobo(?)

Thx for ur guy's help. When you say go the ati site and get the drivers.. i dont understand that. I am not sure if those drivers run on the ubuntu os, do they? so ya, plz help me thx. it is much appreciated. :mrgreen:

---

### Post by Nitrous570 on 2006-01-27
Can ne one help? 

-bump

---

### Post by bscbrit on 2006-01-27
First of all, you might get more info from this forum:

[http://ubuntuforums.org/forumdisplay.php?f=96](http://ubuntuforums.org/forumdisplay.php?f=96)

It specialises in 64 bit.

Secondly, I think (but don't quote me!) that ubuntu will work fine on your box - I wish I had that much computing power available.  I do not know enough about installing 64Bit to offer any advice but the forum above should have plenty.

Yes you can run some windows programs using cedega, but I would suggest that you try using the linux/ubuntu equivalents as well.  Once you get over the initial shock of 'Ubuntu is not Windows' I think that you will be pleasantly surprised.

Running window's games on linux is not recommended but there is a growing band of enthusiasts here: [http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)

Good Luck

---

### Post by aysiu on 2006-01-27
[QUOTE=Nitrous570]
1) will ubuntu, 5.1.0 or whatever it is work on my system.[/QUOTE] Boot the live CD and find out.

---

### Post by towsonu2003 on 2006-01-27
give a try with a 64bit livecd (no installation and no change to harddisk)
[http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/)

for dual core + amd, I think the kernel is called linux-image-k7-smp. you can apt-get it once you decide to install ubuntu using synaptic (under system>administration). I'm very ignorant about that though... so you might want to look around come more in the forums bf installing it.

---

### Post by Nitrous570 on 2006-01-27
[QUOTE=aysiu]Boot the live CD and find out.[/QUOTE]

I have booted the cd. when it goes to about half way done, it says "problem reading from the cd rom. Please make sure it is in the drive. If retrying does not work, please check the intergrity of ur drive"

I click retry, and comes up with the same message. i know that my drive is working fine....could it be cause im runnin on a dual core amd 4400+?

plz help

---

### Post by aysiu on 2006-01-27
It could be a corrupted CD.

---

### Post by Nitrous570 on 2006-01-27
[QUOTE=aysiu]It could be a corrupted CD.[/QUOTE]

k, that is what i thought would be the case. I mean, it seems to be going good until about half way or so. So you don't think it would be because of my dual core processor? (the athlon x2 4400+?)


Ne way, thanks for that assurance. Also, I ordered some live cd's (32 bit, 64 bit, and a mac cd) so i will see if i have ne more luck.

---

### Post by cjm5229 on 2006-01-27
It will probably take 2 or 3 months for the CD's to arrive. Just try burning another cd at the slowest speed your burner will let you burn. Then verify it. Should get you going. Ubuntu for AMD 64 should be a lot better than WindowsXP Windows isn't really set up to run on A 64 bit processor. Ubuntu AMD 64 is. Good luck.

---

### Post by sir_cheats_a_lot on 2006-01-28
> windows is driving me crazy. So unstable, and and ridiculously slow,even with my system. Plz help . thx.  

i certainly hope you installed the 64bit edition of Windows XP and not the standard 32 bit version.  it would explain the problem your were having with it.  you should double check that, because i have never heard of anyone having to down-grade BIOS.

but to answer your questions yes Ubuntu should work with your system, without you messing with your BIOS...you shouldn't of had to with Windows XP either though.

---

### Post by bscbrit on 2006-01-28
I've searched on Google and there appear to be some motherboards that have the correct sockets for AMD64s but require a BIOS update before they will function correctly.  This might be what the OP was referring to...?

---

### Post by xelink on 2006-01-28
all of the athlon X2s work on socket 939, but s939 came out a year before so they need a diferent BIOS to recognice it. athlon 64s are based on the x86_64 architecture. they work in both the 3 and the 64 bit enviroment. If you are new to linux, it would be more practical to install a 32 bit version of linux because it is better supported at the moment(it also is easier to set up because more people are framiliar with it if you need help) 

your proc *SHOULD* be supported fine. your card will be recognized just fine as well, however ATi makes really crudy drivers for linux, so it's like you're only getting half of your potential from your card. I chose the 7800GT over the x1800XL for this reason even though the XL was more efficient powerwise and OC-ed better.

---

### Post by Nitrous570 on 2006-01-28
[QUOTE=sir_cheats_a_lot]i certainly hope you installed the 64bit edition of Windows XP and not the standard 32 bit version.  it would explain the problem your were having with it.  you should double check that, because i have never heard of anyone having to down-grade BIOS.

but to answer your questions yes Ubuntu should work with your system, without you messing with your BIOS...you shouldn't of had to with Windows XP either though.[/QUOTE]


well, when i bought my computer, they told me that windows xp pro is good, well...i guess they failed to realize that i have a 64 bit processor

Maybe that is why I am having some problems? 
Also, sry guys, but how does getting video card drivers for my video card work? are they the same as the ones that i downloaded and installed for windows xp?? also, my mobo drivers? (same as xp again?)
Nother thing, ne viruses for ubuntu? (do i need something like f-prot?)

tx guys  :mrgreen:

---

### Post by xelink on 2006-01-29
I have an Athlon 64 and it runs just ine on XP pro. I would have gottn pro 64, but really the advantage of going up to the 64 bit version isn't that great.

FYI, your processor is based on the x86_64 architecture, you're completely bakwards and forwards compatable.

---

