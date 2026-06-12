---
title: "Wrong screen resolution"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by otherMark on 2006-08-19
I have an NEC MultiSync 1810 lcd monitor which has both a D-sub (normal) and a 5-plug BNC input. This means that I can very conveniently have two computers running and switch the monitor between them by pressing the BNC/D-sub button on the front of it.
(Works fine with windows) 

Problem is, I installed Ubunto with it's puter plugged into the normal D-sub, then changed it to the BNC lead, whereupon the Ubuntu changed the resolution and refresh to minimum (Why?). 
I changed the leads back and now Ubuntu is still using the minimums and I can't find a way to change it back! There are only the minimum options in the menus in system>preferences>screen resolution.

The graphics adapter is an Nvidia MX440, btw.

---

### Post by bodhi.zazen on 2006-08-19
It sounds as if you will need to configure X or edit /etc/xorg.conf.

You need to know you monitor's horizontal and vertical refresh rates.

Also, I am not familiar with your (video) card. Are yoiu using the nvidia or opensource drivers?

---

### Post by otherMark on 2006-08-19
Wouldn't know how to "configure X or edit whatever" (also hate antiquated consoles)
I know my monitor's refresh rates.
The card is an innovision 3d something which uses an nvidia chipset. 
Ubuntu detected everything fine when I first used the d-sub monitor lead. Can't I just run something to re-detect it, now it's back on the normal monitor lead?

---

### Post by otherMark on 2006-08-19
If one can't repair/change resolutions and refresh rates in a few clicks, and one has to arse around with software innards when changing monitors Ubuntu isn't ready for primetime and I have to go back to being windows only. 
Should I change the bios to PnP aware OS - NO ?

---

### Post by GeekSpeek'r on 2006-08-19
yeah, it can be a bit painful sometimes, but in general its all good. What we are looking for is some bas-line data in you xorg.conf file to see if the installer assigned the proper values to your hardware or not.

so, if you would like to continue, please:

cat /etc/X11/xorg.conf

copy and paste it in, and that'll give us a starting point

---

### Post by otherMark on 2006-08-19
I'm doing this in 640x480!
Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"NEC LCD1810"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"NEC LCD1810"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by tseliot on 2006-08-19
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by otherMark on 2006-08-19
Whaaaaat!!!
Do I seriously have to spend the rest of the evening just to install/repair/whatever a bog-standard, run-of-the-mill nvidia driver??? (Thanks for trying to help, but if that's the easiest option for me to be able to use Ubuntu again, then I'd rather forget Linux altogether for another couple of years..., it's exactly the kind of reason I wiped 3 different Suses.)

Don't know how to start doing anything in "point 10", I can only get to xorg in read only via the file menu.

---

### Post by otherMark on 2006-08-19
Isn't there some "detect hardware" button (since apparently PnP doesn't work)? 

I looked at some semi-incomprehensible woffle and complicated jabber in various guides and tried following them but it just comes back with more techno-waffle. Not sure but I may have done something to "xorg" (whatever that's supposed to be) trying to fix it. It still boots in 640x480 and wrong refresh (part of the screen is invisible)
Now what?

---

### Post by otherMark on 2006-08-19
bump

---

### Post by otherMark on 2006-08-19
If there isn't some simple (for a Linux noob) solution to re-detecting the hardware, then it's bye to Linux for another year or three.

---

### Post by Tom Brokaw on 2006-08-19
It's really not too hard, actually.  I broke my GUI the first day I had it trying to configure my LCD's native resolution.  I was also able to fix it the same day thanks to the helpful volunteers on this forum.

However, if you're not comfortable doing it, then Linux probably isn't for you.

---

### Post by bodhi.zazen on 2006-08-19
otherMark: Sorry to see you so frustrated.

What screen resolution do you want?

edit your xorg.conf as follows:

use 
```
sudo gedit /etc/X11/xorg.conf
```

Change:
```
DefaultDepth 24
```

To:
```
DefaultDepth 16
```

Also your monitors section does not have your horizontal and wertical refresh rates. Add this:

```

Section "Monitor"
Identifier "NEC LCD1810"
Option "DPMS"
HorizSync       28-51
VertRefresh     43-60
EndSection
```

> 
Enter your horizontal and vertical refresh rates! Do not just cut and paste these values.

if this works back up your xorg.conf:
```
sudo cp /etcX11/xorg.conf /etc/X11/xorgconf.bak
```

Should take less the 5 minutes

---

### Post by otherMark on 2006-08-19
Ok, I'll try that tomorrow when I'm less annoyed. I'll have to do it all in 640x480 with part of the screen missing....

Thanks for trying to help.

---

### Post by bodhi.zazen on 2006-08-19
Let us know if you need more help.

You can edit the file in a terminal if you like;
(might be easier).


Start with Ctrl-Alt-F1 (Crtl-alt-F7 to return to your GUI).

Log in.

sudo nano /etc/X11/xorg.conf

To save your changes-> Ctrl-X, type Y.

Restart X (Ctrl-alt-F7 -> Crtl-alt-Backspace)

---

### Post by otherMark on 2006-08-20
OK, Day2.
Just came back from a boot sale with two good (and cheap) hard drives, plugged one in (after formatting to ntfs in a windows puter), ubuntu wouldn't boot with it as a slave drive, now won't even boot after unplugging it, so the wrong resolution problem has become irrelevant. Also found out that it's problematic to write data to a windows ntfs drive or partition too, so now I'm deciding wether to forget about Linux for another year or two.
Against: 
There's no MSN compatible that does voice and webcam, 
it's too complicated to share data between xp and Ubuntu and
Ubuntu totally messes up on hardware changes.
I doubt my Pic programmer would work with Linux either, and I likely wouldn't be able to use PicBasic. 
The only thing it might be marginally useful for (to me) is safe web browsing, but since it's apparently (???) aggro to share  data with windows, that goes out the window too.. It's also aggro trying to install all the plugins.
After reading various threads I don't trust it on dual boot in case it messes up windows along with itself.

For:
Don't know, my Ubuntu's crashed. 

Conclusion: I might try another distro but it's crystal clear Linux isn't ready for primetime and 95% of computer users. I really wish it were though.

---

### Post by bodhi.zazen on 2006-08-20
otherMark;

There is a steep learning curve with Linux and Linux is not windows. You are correct in that most windows programs will not run in Linux, however there is a Linux equivalent to most programs as well (although there are exceptions).

It sounds as if you are having hardware issues. In general, it is easier to configure hardware in Ubuntu then Windows. If you get your new drive up and running (with Windows since you are more familiar with Microsoft) you should be able to install Ubuntu (or any other version of Linux) no problem.

Most people migrating to Linux from Windows dual boot until they are familiar with Linux. Linux is, in general, if you are having problems, edit text files rather then plug-and-play and you need to become familiar with permissions and editors.

I suggest you learn a little about GRUB (GRUB boots your box) and configuration of X. At least for me being able to "rescue" my windows partition and configuring X were initial issues for me and my hardware as well. I almost always modify the X configuration after a new Linux install because I get better performance when I do and it takes less then 5 minutes. I get better performance with Lnux and can not perform the same configuration modification in Windows "plug-and-pray".

I also prefer the window managers in Linux (Fluxbox) which is also highly configurable. Yes it took some time, but I have a light, fast, and beautiful desktop with the menu I like and transparency. None of this are even options on my windows XP box at work, although I understand vista is coming...... With Microsoft it is their way or no way.

Just some examples of how and why I pref Linux. As I said, I understand your frustration.

My advice is to dual boot and once you learn Linux you may find it has a little more to offer. GOOD LUCK in any event.

If you would like more assistance please return to the Ubuntu forums. You will find the Ubuntu forums more helpful then the Microsoft help center.

---

### Post by otherMark on 2006-08-20
Thank you for your encouragement.
The computer is fine with xp, so it's not a hardware problem. 
I used grub before with 3 failed attempts at Suse over time, I was thinking of having a computer cleaned of windows, particularly since It's aggro sharing files between these OSs.

Before I give Linux another try I think [COLOR="Red"]Mac OSX on AMD PCs[/COLOR] is worth looking into (do a google[COLOR="Red"]![/COLOR]) ;-). One might well end up with a TRIPLE boot system, and using Grub ;-) : Linux,Windows and OSX

---

### Post by givré on 2006-08-20
Did you try that :
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by otherMark on 2006-08-20
> **givré said:**
> Did you try that :
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
Yes, but I got lost and left it 'till today, whereupon Ubuntu failed completely after I attempted to install a new hard drive first. It never came back so I have removed Ubuntu. 
I'm investigating Mac OSX which can even run on amd pc's now apparently.... if that's not possible, then I might give Linux another try.

Even artists can use MAC OS, so it's got to be the easiest of the three.

---

### Post by givré on 2006-08-20
> **otherMark said:**
> Yes, but I got lost and left it 'till today, whereupon Ubuntu failed completely after I attempted to install a new hard drive first. It never came back so I have removed Ubuntu. 
I'm investigating Mac OSX which can even run on amd pc's now apparently.... if that's not possible, then I might give Linux another try.

Even artists can use MAC OS, so it's got to be the easiest of the three.
Don't think that, on non apple certified material, it's will be quite hard, and even probably impossible.
Good luck 8)

---

### Post by otherMark on 2006-08-20
Do a detailed google and you'll find it looks VERY promising. Somehow I think that would'nt upset the Applecart at all, it would make OSX more popular and hurt M$ in the process.

---

### Post by givré on 2006-08-20
> **otherMark said:**
> Do a detailed google and you'll find it looks VERY promising. Somehow I think that would'nt upset the Applecart at all, it would make OSX more popular and hurt M$ in the process.
Do you know that running ubuntu on a PC looks also quite promissing when googling it.
You'll probably be able to run MacOs, but it'll be quite hard to make some of your hardware running well. Anyway, good luck guy, you'll need it. And come back to tell us how it worked.

---

### Post by otherMark on 2006-08-21
Seems that it's the "modern" processors using SSE3 that are the most suitable for MacOS, so that's out for me too.
Much as I loathe it, xp is what I'm stuck with for the forseeable future. Sorry, but I've had too much aggro with Linux for another while. I also like to change around bits of hardware quite frequently and Ubuntu can't automatically take that in it's stride. I'm sure it's fine for those who happen to get a combination that works and don't change stuff though.

---

