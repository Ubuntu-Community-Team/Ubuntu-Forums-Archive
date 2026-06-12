---
title: "Returning to Ubuntu!"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Sanus Compleo on 2007-11-04
I'm trying, BUT... It seems that I can not install Gutsy for some reason.  I don't know why, but my computer will not boot to the cd, but eventually I used the yellow program in the cd, and that allowed it to boot.  Now... after that, I booted from the cd, and after the usual loading sequence, which I am used to, where it would normally start the OS, all goes black.  I would normally associate this with a graphical error, but the graphics card which I was using never had problems with Ubuntu before, (GeForce MX 4 4000), and maybe it may have been the initial graphics card installed in the mother board.  IDK, but what I need right about now, is like a website or something that will show me everything that's in my computer, so that  I can ask somebody here if anything there doesn't work with Gutsy.

Thanks,
SanCom

---

### Post by tonymoloney on 2007-11-04
Google for Belarc Advisor. Look for the free part and that should do the job.

---

### Post by Sanus Compleo on 2007-11-04
Windows XP Professional Service Pack 2 (build 2600) 	  	IBM 8199Y13
System Serial Number: KCXL2T4
Processor a 	  	Main Circuit Board b
2.40 gigahertz Intel Celeron
8 kilobyte primary memory cache
128 kilobyte secondary memory cache 	  	Board: IBM IBM
Bus Clock: 100 megahertz
BIOS: IBM 24KT54AUS 06/04/2004
Drives 	  	Memory Modules c,d
121.96 Gigabytes Usable Hard Drive Capacity
69.52 Gigabytes Hard Drive Free Space

LG CD-RW CED-8083B [CD-ROM drive]
LITEON CD-ROM LTN486S
3.5" format removeable media [Floppy drive]

Maxtor 6Y080P0 [Hard drive] (81.96 GB) -- drive 1, s/n Y32NR2TE, rev YAR41BW0, SMART Status: Healthy
ST340014A [Hard drive] (40.02 GB) -- drive 0, s/n 5JXCNS9V, rev 3.10, SMART Status: Healthy 	  	510 Megabytes Installed Memory

Slot 'J6J1' has 512 MB
Slot 'J6J2' is Empty
  	Local Drive Volumes
  	
		
c: (NTFS on drive 0) 	40.01 GB 	24.91 GB free
f: (NTFS on drive 1) 	81.95 GB 	44.61 GB free
  	Network Drives
  	None detected
	  	
Microsoft Office Document Image Writer Driver 	on Microsoft Document Imaging Writer Port:
Controllers 	  	Display
Standard floppy disk controller
Intel(R) 82801DB Ultra ATA Storage Controller - 24CB
Primary IDE Channel [Controller]
Secondary IDE Channel [Controller] 	  	Intel(R) 82845G/GL/GE/PE/GV Graphics Controller [Display adapter]
NVIDIA GeForce4 MX 4000 [Display adapter]
Compaq CPQ TFT5010 [Monitor] (15.2"vis, s/n 018BH34PK054, May 1990)
HP L1506 [Monitor] (14.9"vis, s/n CND73019LG, July 2007)
Bus Adapters 	  	Multimedia
Intel(R) 82801DB/DBM USB 2.0 Enhanced Host Controller - 24CD
Intel(R) 82801DB/DBM USB Universal Host Controller - 24C2
Intel(R) 82801DB/DBM USB Universal Host Controller - 24C4
Intel(R) 82801DB/DBM USB Universal Host Controller - 24C7 	  	SoundMAX Integrated Digital Audio
Communications 	  	Other Devices
HSFi2002 56K Data Fax Modem

		
Intel(R) PRO/100 VE Network Connection
 primary  	Auto IP Address: 	192.168.1.101 / 24
	Gateway: 	192.168.1.1
	Dhcp Server: 	192.168.1.1
	Physical Address: 	00:0D:60:A7:F5:AF
 
Networking Dns Servers: 	64.233.222.2
64.233.222.7
	  	Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
PS/2 Compatible Mouse
USB Root Hub (4x)
Virus Protection [Back to Top] 	 
Total Protection for Small Business Version 4.5.0.464
    Realtime File Scanning On
avast! antivirus 4.7.1043 [VPS 071104-0] Version 4.7.1043
    Realtime File Scanning On
	 













Oi, srry for the long post, but would any of this stop Gutsy from working?

---

### Post by Sanus Compleo on 2007-11-04
Oh, by the way, I'm trying to install Ubuntu on the Maxtor hard drive, and keep xp on the other one, which is the current one that I can even use.  The Maxtor was from a differant computer, and I already pretty much got everything old that I wanted off of it.  Would I need to reformat the hard drive, or not?

---

### Post by Can+~ on 2007-11-04
> **Sanus Compleo said:**
> Oh, by the way, I'm trying to install Ubuntu on the Maxtor hard drive, and keep xp on the other one, which is the current one that I can even use.  The Maxtor was from a differant computer, and I already pretty much got everything old that I wanted off of it.  Would I need to reformat the hard drive, or not?

Yes. Ubuntu (and linux in general) needs EXT3. So your plan is have the first Hard disk for windows, the WHOLE maxtor for ubuntu?

I suggest to reinstall from the LIVECD into the maxtor hdd. 

> I don't know why, but my computer will not boot to the cd

Won't boot to the CD? If it's not even loading, then you should change the boot order on the BIOS. Reboot and start hitting SUPR (or the key that appears on the screen to enter the bios.. duh). Then change the boot order, making sure the CD/DVD reader is on top of the Hard disk.

If it loads the CD, but won't load the interface, then you can jump into the terminal (Ctrl+Alt+F1), and run pretty much any command from there. I had a similar problem, but somehow, I restarted the xorg and booted alright, you should give it a try. Jump to the terminal on the LIVECD, and then use:

> sudo /etc/init.d/gdm restart

It worked magically for me.

---

### Post by tonymoloney on 2007-11-05
I'm assuming that your Maxtor jumper has been set to slave if it's running from the second connection on the primary IDE cable? If not, that needs fixing also.

---

### Post by Sanus Compleo on 2007-11-05
Actually, the maxtor had been set to slave, when I had put in a much smaller hard drive, and installed edgy on that one.  Which is dead now... sosad.  I'm going to try what Can+~ said really quickly, then reply with my results here.

---

### Post by Sanus Compleo on 2007-11-05
Alright, cool, alot of stuff happened, and even more stuff didn't happen.  I started it, and went to command line before trying to boot, and put in the gdm restart thing, but it didn't recognize any commands put in.  Not even sudo etc.  Second off, when I started in graphics safe mode, I basically got this:

```
Starthing Deferred execution scheduler atd
Starting periodic command scheduler crond
Checking battery state...
Running local boot scripts (/etc/rc.local)
```

All had a little [OK] to the right, and a * to the left.  I tried the sudo... gdm restart thing, and it didn't do anything, not even say that it didn't not recognize the command.  Even if I put a bunch of random words in, it wouldn't say that.

Restarted the computer, and it did the usual shutdown thing it does in graphics safe mode, and started again in normal mode, and tried to put in the gdm restart command before it did anything else, (BTW, I pressed the super key all before this point, while trying to start normal mode [Oh, and I already had it set up to try and boot from the CD first, and it allowed me to select Ubuntu - Linux from the OS selection]) but the whole screen went black before I could type it in. (I'm 75 wpm, and it did not give me time to type that in)  Anybody else got an idea by any chance?

Thanks to you two guys, but that didn't seem to fix me problem sofar...









Edit:  Oh, and when I started up windows, it brought up the windows ubuntu install program, which said: "Ubuntu is already installed, do you want to uninstall it?"  Below it said: "F:\ubuntu will be uninstalled"

---

### Post by Sanus Compleo on 2007-11-05
Hey, anybody still interested in helping me?

---

### Post by TeaSwigger on 2007-11-05
Patience it's all just us regular folks here y'know ;)

I have Intel(R) 82845G/GL/GE/PE/GV Graphics Controller [Display adapter] in my 2nd PC. It is a pain in the you know what. If it's trying to run that instead of your groovy good graphics card, it'll hang up if it acts at all like mine. 

Be back in a tick.

---

### Post by TeaSwigger on 2007-11-05
Why people try calling my on the phone at this hour I have no idea. Anyway where were we...

Try to ensure the good graphics card is being used instead of the integrated one. Do you know how to enter and use your computers' BIOS? If you can, look for anything which would select what graphics card is used (onboard, what have you). If it isn't set to auto, and you can do so, try it. If this doesn't work try selecting the good card if possible. If that doesn't work see if you can set the amount of memory for graphics to something higher (not an option on mine, no idea about yours). Look for any other things amiss.

Striking out left and right there, if you're stuck with that intergrated card until you can get gutsy installed, it could be the limitation. You might be obliged to use the Alternate Install CD, which among other uses can work around just such a problem because it doesn't demand much from the graphics. Once installed, disable to usplash in GRUB (you're sure to find how to do that searching at these forums, or post back) until you have it running with the groovy good card. Otherwise it *may* freeze on a black screen, flash noise on screen during shutdown and hang or other weird stuff. There's a way to get it working with the integrated graphics if you're really stuck but don't bother till/if it gets to that.

PS as you may be gathering, ubuntu has ntfs-3g, a feature to allow it to read and write to XP's NTFS format, and there's a driver you can install in XP that will let it read and write to the linux-formatted drive. It's free and works fine. So format drives/partitions you plan to use for linux in its recommended format (ext3) and keep XP's own partition (or drive) in its own recommended NTFS.

---

### Post by Sanus Compleo on 2007-11-05
Hmm...  Well my windows was using both, (Dual screen [so unecessary]) and thankfully the geforce was detected as plug and play, but I still did need to install drivers.  I'm going to check the BIOS settings and see if I can't direct everything to just the geforce, and if that doesn't work, to the integrated, which I'm sure will prolly have no problem with it.  If that doesn't work, then well I'll reformat the new hard drive, and unplug the master, and then work with it from there, but that will be a last resort.  I'll look into the drivers which allow the whole cross platform writing thing, if I still can't get it to work.  (OH BTW, I do beleive that the maxtor has windows xp pro, which doesn't allow xtra partitions, so i'll prolly have to reformat the lil S.O.B.)

Well, I'll give a status report later, after I get back on me own comp.

---

### Post by Sanus Compleo on 2007-11-05
Alright, I've found out some cool stuff.  First off, AGP onload, uses my nvidia card, while integrated onload uses only the integrated, (who'da guessed?) turns out, that using the integrated graphic output settings or whatever, I got to the part where the mouse is.  Yay, a step closer to the majesty that is linux.  Alright, I tried to reset gdm like twice, which didn't quite work.  I'm almost to my last resort option, does anyone have anything else to suggest before I gut this behemoth of a computer?

---

### Post by ByteJuggler on 2007-11-05
Suggestion: Do a CD verification/check to ensure the computer can read the CD.

---

### Post by Sanus Compleo on 2007-11-05
How would I go about that?

---

### Post by TeaSwigger on 2007-11-05
Perhaps ByteJuggler means the disk test you can run when you start the ubuntu CD, it does a self-test to ensure that disc will be read by that drive perfectly. If there's a problem try another disc, burn at a slower speed, etc.

---

### Post by Sanus Compleo on 2007-11-05
I'll try that, BUT I think that I may have to go with the alternative disk.

Oi, it says it'll take a little over an hour...

Btw, can a person show off their artwork in the Digital Art section?  I don't know where to find the rules, because I'm not used to this forum software.

---

### Post by TeaSwigger on 2007-11-05
> **Sanus Compleo said:**
> I'll try that, BUT I think that I may have to go with the alternative disk.

I suggest trying the alternative CD, absolutely, in case it's that integrated graphics card hanging things up. Keep at it and you shall be victorious ;) Gotta turn in here, good luck to ya.

---

### Post by Sanus Compleo on 2007-11-05
Alright, and thanks for helping me out.

---

### Post by ByteJuggler on 2007-11-05
> **TeaSwigger said:**
> Perhaps ByteJuggler means the disk test you can run when you start the ubuntu CD, it does a self-test to ensure that disc will be read by that drive perfectly. If there's a problem try another disc, burn at a slower speed, etc.

Correct, sorry I wasn't being clear on that.  :-)

---

### Post by Sanus Compleo on 2007-11-05
Alright, I just got the alternative disk, now what do I do?  I booted to it earlier, and it gave me a command line, which I'm not really all that good with :P

---

### Post by Sanus Compleo on 2007-11-05
YAY!  I used the original disk I wrote, and just decided to go in the other room and watch a cartoon.  THEN!  It worked.  I'm installing it right now!  YAY!  BUT... I've got another question... How do you set up Ubuntu to work with two moniters at the same time?

---

### Post by TeaSwigger on 2007-11-06
Yay!

I've no idea about the dual monitors. Many folks are doing it though, made especially nifty by the multiple desktops in ubuntu. Anyway just wanted to say congrats :guitar:

---

### Post by Sanus Compleo on 2007-11-06
I love flukes, but I decided to go back, and make sure that I've got everything I wanted off of the old hard drive.  (It had my CS2 on it [I'm an avid gimp user, but keep the program around incase I want to ever learn it])  But man... 80 gigs of stuff, that will never see the light of day again...  It'll be alot of combing through stuff.

---

