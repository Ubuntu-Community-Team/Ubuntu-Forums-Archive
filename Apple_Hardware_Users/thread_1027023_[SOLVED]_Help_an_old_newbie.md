---
title: "[SOLVED] Help an old newbie"
date: 2008-12-31
forum: Apple Hardware Users
---

### Post by djacks01 on 2008-12-31
Some basics about my situation:

This is my Mac G4 AGP:


Report Created:12/31/08 at 12:09:45 PM

Software overview
	Mac OS overview
		Finder:	9.2
		System:	9.2.1  US
	Note: No startup disk was selected.
Memory overview
	Disk cache:	8160K
	Virtual memory:	is off
	Built-in memory:	1.12 GB
	Number of empty RAM slots: 0 ()

Internal ATA 2
		ID = 0
				Hard drive
					Driver version:	3.2.5
					Mac OS partitions:	1
					Removable media:	No           
					Size:	27.40 GB (1K = 1000)
					Capacity:	25.53 GB (1K = 1024)
				
					MacHD
						Volume format:	Mac OS Extended (HFS+)
						Capacity:	25.53 GB
						Available:	5.39 GB
						Percent full:	78 (Mac OS)

		ID = 1
				Hard drive
					Driver version:	3.2.5
					Mac OS partitions:	1
					Size:	79.97 GB (1K = 1000)
					Capacity:	74.50 GB (1K = 1024)
				
					MacOS/Preferred LinuxPPC
						Volume format:	Mac OS Standard (HFS)
						Capacity:	100 MB
						Available:	98.3  MB
						Percent full:	98 (Empty)
				
	PCI
		SLOT-A (AGP)
				Display card
					Card type:	display
					Card name:	ATI,Rage128Ps
					Card model:	ATI,Rage128Pro
					
				
						Display
							Screen Size (pixels):	800 x 600
							Grays/Colors:	Millions
							Resolution (dpi):	72 x 72
							Additional Information:	Main screen



Attempting to install  Ubuntu on the second drive or at least run live cd mode to check it out.
(I did this on an old dell and had no major problems - but gave this dell to a friends 7 year old for Christmas - she loves it!)

So, I downloaded : ubuntu-8.04.1-desktop-power.iso
It is on the desktop and I haven't a clue about the next step. I've tried to parse out the lingo of MacPPC Install and can not get anywhere. Have studied yaboot docs , Open Firmware docs, How to burn ISO to CD docs but seem to be very far from understanding what to do next. I am going around in circles and am dizzy.

My plea: tell me what do I need to study/understand in order to install to mac or to run from the live cd. Point me in the right direction please.  I worked with mac exclusively from 1985 to 1995 then went over to the dark side and trying to get back to mac (especially this old OS) is harder that I thought.

Thanks,

---

### Post by mkvnmtr on 2008-12-31
To boot the live disk you need to of course put it in. Restart while holding down the "c" key. Keep it held down until two icons come up on the screen. One Mac the other Linux. then you can let up on the key. When the little circle stops turning click on the linux icon. When the first words come up on the screen press the tab key. This should show you several options to type in. On mine I need to type in "live-nosplash-powerpc". If that one doesn't work for you then try another of those listed. If it works you just have to wait until the disk gets read and the desk top will come up.If your internet is connected you are then set to go.
Later if you decide to install you should probably start another thread to get some tips on installing after partitioning youor hard drive.

---

### Post by caladan1810 on 2009-01-01
Welcome to the Force my Padawan Learner.

You need the correct .iso file to burn to cd. 
You have listed ubuntu-8.04.1-desktop-power.iso.

Check out the following it is for Mac (PowerPC) and IBM-PPC (POWER5) desktop CD. Download the .iso.
[http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-desktop-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-desktop-powerpc.iso)

Once you have the .iso you need to Open your CD Burner program & select burn image file to cd. Once you have done that. **Back up what what you need**. 

Then place the CD with the ubuntu-8.04.1-desktop-powerpc.iso you just burned in the CD-ROM and press 'C' while rebooting, it will then boot from CD. When it does you'll be presented with a text menu at the prompt as the oher poster mention press the tab key it will give you a list of options start the Live CD. select one, tt will then load the Live CD.  Hope this helps. Lets us know how you go.

---

### Post by djacks01 on 2009-01-01
Thank you. At this point I have burned the correct .iso file to a cd. Placed the cd in drive and pressed "Option" while rebooting. (this is an older keyboard from an original iMac) I have now on the screen what looks like a "refresh" circle/arrow, a MacHD pict, and a straight/arrow pointing right. I assume retry, choose to boot from mac HD, and reboot Mac. There is no choice to boot from cd. Question. Is the mac not able to see the cd to boot from iso?  thanks again.  D

---

### Post by mkvnmtr on 2009-01-01
We need to check that you burned the ISO as an image. When you are in Mac and click on the disk do you see one file labeled Iso or do you see many files?

---

### Post by djacks01 on 2009-01-01
There is one file labeled ISO

thanks,

---

### Post by mkvnmtr on 2009-01-01
Then you have just copied the file. You need to burn an image to get it to boot. I don't have my Mac up but as I remember you just need to add the iso from your desktop to Disk Utility and burn. Iklill close my Ubuntu and start my mac system so I can refresh my memory and come back with what I find.

OK I am on my mac. When you open Disk Utility click on the burn button. Choose the iso in the window that comes up. Click open and a window comes up that says insert disk. When you insert the disk As I remember you only have the option to burn. It is best to burn it a slowly as possible but I have never found a speed option on my disk utility. It is also best to use a cd read only disk.

---

### Post by djacks01 on 2009-01-01
Thank you forum "Apple Users." Am writing this from Firefox on my Mac G4 using Ubuntu. You have helped me tremendously and given me a new project to explore.  :popcorn:

---

