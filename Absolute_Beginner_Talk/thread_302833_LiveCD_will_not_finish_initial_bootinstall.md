---
title: "LiveCD will not finish initial boot/install"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Allessess on 2006-11-19
Ok, I just pulled a newb and lost the long message I was typing so I'll keep it short.

CD loads up to point where it has passed teh back and forth orange pong bar...

Moves on the the left to right progress bar and gets to what appears to be about 95% plus...

Stops doing anything(that you can SEE), however if you start typing you can see that in fact it's at a prompt of some kind(though the prompt is garbled) because you will see a small green line being created where you know it's the text you are typing. Obviously it's a display issue that happens at that final stage(I'm a newb...loading the "X window"?).

I'm not afraid of a command prompt/shell/terminal or whatever else you want to call it. 

So the question is, is there a way to drop the pretty and get to where it will display just the text so I can give you guys some errors to help me with?

I've heard a lot of hype about linux for YEARS and a lot recently about Ubuntu...I'm really hoping to get this loaded and broaden my computing landscape.

Any help is GREATLY appreciated.

Thanks,

Allesses

Oh and system info incase there are any caveats I should be aware of once we get to a prompt...
          Board: ASUSTeK Computer INC. P5GDC Rev 1.xx
          Bus Clock: 200 megahertz
          BIOS: American Megatrends Inc. 1011.005 10/13/2005          
          Card name: RADEON X700 Series   
          Manufacturer: ATI Technologies Inc.
          Chip type: RADEON X700 PRO (0x5E4B)
          DAC type: Internal DAC(400MHz)
          Display Memory: 256.0 MB
          Processor: Intel(R) Pentium(R) 4 CPU 3.00GHz HT
          Memory: 1024MB RAM
          Intel(R) 82801FB Ultra ATA Storage Controllers - 2652
          Intel(R) 82801FB/FBM Ultra ATA Storage Controllers - 266F
          Linksys NC100 Fast Ethernet Adapter 
          Marvell Yukon 88E8053 PCI-E Gigabit Ethernet Controller

---

### Post by b_martinez on 2006-11-19
Try booting with the line "xdrvr=vesa" at the boot prompt.Just don't type the  quotation marks ( "" ).  you can maybe even add a resolution line, but I'm not sure how.
hth
Bill

---

### Post by xpod on 2006-11-19
Try "safe graphics mode" at boot up....then if that fails and your not bothered about the "prettys" and just want it installed then mabey the alternate cd would be your best bet..

You would`nt be able to test it first like you can with a live cd as i`ts only an installer but it sometimes finds installing a whole lot easier.

[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

further down the page

Of course there could be any number of reasons why your live cd aint loading so it would be best try all your options with that first.

Good luck

---

### Post by rlozano on 2006-11-19
agree with xpod. use safe booth. its your best option specially if you feel that the problem is somehow related to display.

---

### Post by Allessess on 2006-11-19
hrm...same thing happens in safe boot

I tried using the command you listed but it just booted up xp so I'm obviously missing something there...

Currently downloading the alternate install CD.

Oh and I did the CD and memory checks and they both came back golden so that's that.

Just mentioning it cause after reading through several other similar forum threads there seems to be a consensus to do those two things.

I just wish I still had a second pc to make this easier...

Any suggestions on how or what to run from the alt install CD since I'm already having problems?

And thanks for responding so quick.

---

### Post by spandon on 2006-11-19
Hi,
I had similar problems with the Edgy (ubuntu 6.10)Live Cd on two of my machines (laptop and a desktop) both had ati cards.
I did the following to load the live cd and then to install:

**Live CD**
when the booting the disk, at the first, press escape, you will then get a message stating that you are leaving the graphical boot etc, press enter.
at the boot: prompt enter
**live vga=771 noapic nolapic** (exactly as written) and press return.
the disk then loads up edgy and I get a screen resolution of 1280x1024 plus alternatives.

If this works and you want to install, then you have to use the Alternative CD, and to install it, at the boot: prompt enter
**install vga=771 noapic nolapic**, then edgy installs.

This worked for me, give it a try using the Live CD, if this works then the installation will also work (using the Alt CD)
Good luck
Don

---

