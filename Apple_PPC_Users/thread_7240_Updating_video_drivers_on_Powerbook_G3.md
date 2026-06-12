---
title: "Updating video drivers on Powerbook G3"
date: 2004-12-05
forum: Apple PPC Users
---

### Post by monkeyshaman on 2004-12-05
It's me again, Margaret..... :-P 

Even though everthing seems to be running pretty good, there's a problem with the video.  There is a line running down the left side of the screen that is kinda "garbled".  It's only about 1/4" or less wide and doesn't interfere with anything on the screen, but I'm afraid it might damage the screen over time.  I tried to do an update of the ATI video drivers, per the post about "tweaking" your Ubuntu install, but it says the file (fglrx-driver) can't be found.

Anyone got a clue how I can fix it?

Arnold

P.S.
Here's something that I don't THINK would be the cause, but ya never know.  The display is 13.3" and they seem to have an "inherent defect" involving the video data cable.  I know this laptop has that problem, because the video will start to go bad, but if you squeeze the display casing on the left side it straightens out.

---

### Post by Viro on 2004-12-05
Do not try to install the fglrx driver. It's only for x86 based machines (i.e. PCs). Post the contents of your /etc/X11/XF86Config-4 file and we'll see what's up.

---

### Post by spence on 2004-12-06
[QUOTE=monkeyshaman]It's me again, Margaret..... :-P 

Even though everthing seems to be running pretty good, there's a problem with the video.  There is a line running down the left side of the screen that is kinda "garbled".  It's only about 1/4" or less wide and doesn't interfere with anything on the screen, but I'm afraid it might damage the screen over time.  I tried to do an update of the ATI video drivers, per the post about "tweaking" your Ubuntu install, but it says the file (fglrx-driver) can't be found.

Anyone got a clue how I can fix it?

Arnold

P.S.
Here's something that I don't THINK would be the cause, but ya never know.  The display is 13.3" and they seem to have an "inherent defect" involving the video data cable.  I know this laptop has that problem, because the video will start to go bad, but if you squeeze the display casing on the left side it straightens out.[/QUOTE]
 Do you pass any kernel arguments through BootX?

---

### Post by monkeyshaman on 2004-12-06
[QUOTE=Viro]Do not try to install the fglrx driver. It's only for x86 based machines (i.e. PCs). Post the contents of your /etc/X11/XF86Config-4 file and we'll see what's up.[/QUOTE]

I figure you didn't want to see the WHOLE XF86Config file, so I just cut and pasted the section about the video and monitor.


[COLOR=Indigo]Section "Device"
	Identifier	"ATI Technologies, Inc. 3D Rage LT-G (215LG)"
	Driver		"ati"
	BusID		"PCI:0:17:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	28-49
	VertRefresh	43-72
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage LT-G (215LG)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection[/COLOR]

Any advice you can give would be greatly appreciated.  Thanks again!  :grin: 

Arnold

---

### Post by monkeyshaman on 2004-12-06
[QUOTE=spence]Do you pass any kernel arguments through BootX?[/QUOTE]
 I didn't try any kernel arguements.  Think that might help?  Any suggestions on what to use?

Thanks,

Arnold

---

### Post by monkeyshaman on 2004-12-06
I just tried the arguement "video=atyfb:vmode:14" and that didn't seem to have any effect on it.

---

### Post by Viro on 2004-12-06
Somethings for you to try. I think that might be caused by incorrectly specifying the refresh rate. Try these :

HorizSync       30-70
VertRefresh     50-160

They work on an iBook with a ATI chip just fine, so they might work on your machine. Also, you might want to comment out the line Option "UseFBDev" "true" by adding a # before the line. I don't think people normally use FBDev.

---

### Post by monkeyshaman on 2004-12-06
[QUOTE=Viro]Somethings for you to try. I think that might be caused by incorrectly specifying the refresh rate. Try these :

HorizSync       30-70
VertRefresh     50-160

They work on an iBook with a ATI chip just fine, so they might work on your machine. Also, you might want to comment out the line Option "UseFBDev" "true" by adding a # before the line. I don't think people normally use FBDev.[/QUOTE]
 
Tried that, but it didn't help.  Thanks though.  :)

Any other suggestions?

Arnold

P.S.
I did find out that when I change the screen resolution from it's max (1024x768) to a lower res, the garble goes away.  I have the res set at 1024x768 when I boot into Mac OS and I don't get the garble.

---

### Post by spence on 2004-12-06
I've got the same problem on my Wallstreet PB.  It looks like the pixels that form the "at" in Applications are jumping all around.  I vaguely remember this happening with Gnome  when I was using another Linux distribution as well.  I ended up dropping gnome and going to just a WM (for other reasons).  Maybe I'll try that here and see if the problem goes away.  If it does then we've at lease narrowed our search to Gnome (which is not a huge help but is something.)

Spence

---

### Post by monkeyshaman on 2004-12-06
[QUOTE=spence]I've got the same problem on my Wallstreet PB.  It looks like the pixels that form the "at" in Applications are jumping all around.  I vaguely remember this happening with Gnome  when I was using another Linux distribution as well.  I ended up dropping gnome and going to just a WM (for other reasons).  Maybe I'll try that here and see if the problem goes away.  If it does then we've at lease narrowed our search to Gnome (which is not a huge help but is something.)

Spence[/QUOTE]
 That's EXACTLY what is happening with my laptop.  Starts at the "at" of Applications and goes all the way down the screen.  Let me know if you have success changing to another WM.

Arnold

---

### Post by monkeyshaman on 2004-12-07
I did find out that when you install Yellowdog on the laptop, it says the Horz is 119.0kHz and the vert is 196.0kHz.  I tried that on my Ubuntu install and that didn't really change anything.

Oh well. :(

Arnold

---

### Post by slux on 2004-12-07
You could just copy the XF86Config generated by Yellow dog to your Ubuntu install if that one's working all right.

---

### Post by Viro on 2004-12-07
Look at this guy's XF86Config file. Perhaps it'll shed some light on what's going on? [http://www.desertsol.com/~kevin/ppc/newest/XF86Config-4.3.0-r6](http://www.desertsol.com/~kevin/ppc/newest/XF86Config-4.3.0-r6)

---

### Post by monkeyshaman on 2004-12-07
Is that config file being run on a Wallstreet G3?

---

### Post by monkeyshaman on 2004-12-07
[QUOTE=slux]You could just copy the XF86Config generated by Yellow dog to your Ubuntu install if that one's working all right.[/QUOTE]
 I'm only running a 4 gig drive, so that would require deleting Ubuntu, reinstalling Yellowdog, copying the XF86Config file.....THEN deleting Yellowdog again and REINSTALLING Ubuntu on the laptop....All for something that MIGHT work?

Think I'll try other options first.  This will be my "last resort". ;)

Thanks for the advice, though.

Arnold

UPDATE!!!!
Well, I tried using the XF86Config settings in Yellowdog for Ubuntu.  Let's just say I'm glad I made a backup copy of the XF86Config-4 file BEFORE I made the changes.  Couldn't boot into X afterwards.  :(

Oh well....Back to the drawing board.

---

### Post by monkeyshaman on 2004-12-07
I think I found a program that can help with the video problem.  It's called Xeasyconf and is a PPC only program for configuring XFree for the PPC.  Only problem is I can't seem to find anywhere to download it.  Most links are dead and the only distro I find it with is the PPC version of Gentoo.   :-x 

Anyone else got an idea of how I can get this "magickal" program and get it installed on my laptop?

Arnold

---

### Post by spence on 2004-12-08
You can download the source at

[www.ibiblio.org/gentoo/distfiles/xeasyconf-0.1.5.tar.gz](http://www.ibiblio.org/gentoo/distfiles/xeasyconf-0.1.5.tar.gz) 

but I've tried it and it didn't remove the pixel jump.

---

### Post by monkeyshaman on 2004-12-08
[QUOTE=spence]You can download the source at

[www.ibiblio.org/gentoo/distfiles/xeasyconf-0.1.5.tar.gz](http://www.ibiblio.org/gentoo/distfiles/xeasyconf-0.1.5.tar.gz) 

but I've tried it and it didn't remove the pixel jump.[/QUOTE]

Then I hate to say it, but it HAS to be a problem with the video drivers in Ubuntu.  That is the only reason I can find why another distro like Yellowdog would work just fine, but Ubuntu would have trouble, even though the settings in both looked to be exactly the same.  I can reduce the resolution to 800x600 or even 640x480 and the jumping goes away.  But I don't really want that.   :-( 

Oh well....Hopefully I'll figure out something soon.

---

### Post by monkeyshaman on 2004-12-08
[QUOTE=spence]You can download the source at

[www.ibiblio.org/gentoo/distfiles/xeasyconf-0.1.5.tar.gz](http://www.ibiblio.org/gentoo/distfiles/xeasyconf-0.1.5.tar.gz) 

but I've tried it and it didn't remove the pixel jump.[/QUOTE]

Well I can't even get the stupid program to install.   :mad: 

Yellowdog is beginning to look better and better right now.  :cry:

---

### Post by monkeyshaman on 2004-12-10
Well, I tried using the XF86Config settings in Yellowdog for Ubuntu. Let's just say I'm glad I made a backup copy of the XF86Config-4 file BEFORE I made the changes. Couldn't boot into X afterwards.

Oh well....Back to the drawing board.

---

### Post by spence on 2004-12-10
[QUOTE=monkeyshaman]Well, I tried using the XF86Config settings in Yellowdog for Ubuntu. Let's just say I'm glad I made a backup copy of the XF86Config-4 file BEFORE I made the changes. Couldn't boot into X afterwards.

Oh well....Back to the drawing board.[/QUOTE]
 I've now seen two posts on old BBs/usenet where people using Debian had the same problem, but neither of them had answers posted.  I have e-mailed one of the posters and I'll see if I can do the same for the other.

---

### Post by spence on 2004-12-10
I finally got the garbled line to dissappear.  At the BootX prompt pass the following arguments:

video=atyfb:vmode:14,mclk:71

That did it for me anyway.  I didn't have the "mclk:71" before but adding it seems to have solved the problem.

---

### Post by monkeyshaman on 2004-12-10
[QUOTE=spence]I finally got the garbled line to dissappear.  At the BootX prompt pass the following arguments:

video=atyfb:vmode:14,mclk:71

That did it for me anyway.  I didn't have the "mclk:71" before but adding it seems to have solved the problem.[/QUOTE]

Great!  I'll give that a try when I get home.   ;-) 

Arnold

---

### Post by monkeyshaman on 2004-12-10
AND THERE WAS MUCH REJOICING IN THE WORLD!!!!!! :)

That worked!  The pixel jumping is gone!  So what is "mclk:17" anyway?

Arnold

P.S.
Ok...Now I'm going to break it by upgrading to Hoary.  LOL!

---

