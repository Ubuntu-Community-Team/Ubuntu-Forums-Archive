---
title: "Ants Screensaver hangs Ubuntu"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by gantww on 2006-09-11
Hello all,
I was attempting to find a worthy screensaver for my new Ubuntu box, and it completely hung up on the AntSpotLight and a couple of other screensavers. The hang up was so complete that I had to do a hard reboot. I can't remember what type of video card it has in it, but I suspect that it is the problem. What information do you need to help me?

---

### Post by gn2 on 2006-09-11
Why bother with a screensaver?
Set it to blank screen and set the monitor to switch off using the power management options. This will save your screen and electricity.

---

### Post by XPuntu on 2006-09-11
Some people like their screensaver to come on very quickly for privacy reasons you know, like when they're called away from their desk or going to the bathroom.

Cheers

---

### Post by gn2 on 2006-09-11
Setting the blank screen option gives you a screensaver that is a plain black screen, so works like an ordinary screensaver. Without the hangups.

---

### Post by Fully216 on 2006-09-11
You might want to figure out what video card you have.  If you are using some of the advanced features of your card, you need to have the proper driver installed.  This is my personal experience with dealing with my nvidia card (using the 'nv' driver versus the one off their webite).  Try running 'lspci' or looking at xorg.conf to see what card you have.

---

### Post by metal_ike on 2006-09-11
I'm having similiar troubles with screensavers plus other random things.  The Fiberlamp screensaver hangs the OS for sure but annoyingly enough it also hangs in other seemingly random places.  There's probably a connection between them though I've got no idea what it may be.

This is my video card according to lspci:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

These happen from a fresh install even, and while its not state of the art my computer is a ways off from garage sale fodder.  I really like Ubuntu but these hang-ups are seriously cheesing me off, so any help would be appreciated.

---

### Post by Fully216 on 2006-09-12
Have you tried to install the drivers listed on ati's website?  I am not too familiar with their cards, but they do offer linux support.  You can find a list of the available drivers at:

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

From what I have read though, the proprietary Linux drivers don't support the R100 chips (Radeon 7000-7500), which is why it is listed as 8500 or higher on their website.  Linux users have the option of both the proprietary (R200 and above) and open source (R480 and below) drivers.

I am guessing because there is no driver available for your specific chipset, you will not be able to use some of the more fancy features of the card like 3D acceleration.  This  was the case with my nvidia card.

You could try 'sudo dpkg-reconfigure xserver-xorg' and see if that helps.  I would also like to see the xorg.conf to see what the exact settings are.

---

### Post by gantww on 2006-09-12
Here's what I got from lspci:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 06)
0000:00:0d.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 06)
0000:00:0e.0 Ethernet controller: 3Com Corporation 3cSOHO100-TX Hurricane (rev 30)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]


As you can see, I have a similar problem to the other guy. How do I figure out what I really have?

---

### Post by djsroknrol on 2006-09-12
I've had very good luck with the Radeon driver thru Synaptic...you guys might try it out. It claims support all the way down to the 7200 and I'm running all kinds of goodies with it...

---

### Post by Fully216 on 2006-09-12
Thanks for the lspci post.  

"0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]"

It is interesting; ubuntu thinks you have the 8500 card.  Are you sure of your model?  If so, this might because it doesn't offically support anything lower than the r200 chipset, and most of the chipset will be reverse compatable.

I would try the suggested synaptic driver first before we try to hack it a bit.  There is a good article about it here.  It is a little old considering it is conserned with a different card and version Edgy, but the basic ideas will help.

[http://www.marteydodoo.com/2006/08/29/installing-binary-ati-drivers-on-ubuntu-edgy/](http://www.marteydodoo.com/2006/08/29/installing-binary-ati-drivers-on-ubuntu-edgy/)

The other option is a driver hack, which might make your system unstable.  I hope this helps.

---

### Post by zephyrus17 on 2007-12-25
Sorry for the Necro-posting, but I've been having the same problem.

Often, when the screensaver comes on, I can't revive the screen. And when I try to go to Preferences -> Screensaver, it immediately logs me out of Gnome, into the login screen, which means I can't change the screen saver. (Scrensaver's not 'Blank')

I don't know if this is related, but, even though I'm actually using an ATI Xpress 1150, lspci is saying that I'm using a
> 01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
A 1100, not 1150.

Is that normal?

---

### Post by Moop on 2007-12-25
It could be that you don't have 3D enabled on your video card and any 3D screensaver will crash. Do you have the restricted drivers installed?

You can check this thread for a method of resetting your screensaver to default. 
[http://ubuntuforums.org/showthread.php?t=406267&highlight=disable+screensaver&page=2]("http://ubuntuforums.org/showthread.php?t=406267&highlight=disable+screensaver&page=2")

---

### Post by Ux64 on 2007-12-25
> **gantww said:**
> Hello all,
I was attempting to find a worthy screensaver for my new Ubuntu box, and it completely hung up on the AntSpotLight and a couple of other screensavers.

I had similar problem with Live CD. But when I installed native display adapter drivers I got rid of that problem.

And I were using 64 bit version.

---

### Post by Ux64 on 2007-12-25
> **Moop said:**
> It could be that you don't have 3D enabled on your video card and any 3D screensaver will crash.

Yeah. But it naturally shouldn't take whole OS with it. ;) It sounds more like one rival operating system. ;)

---

### Post by Moop on 2007-12-25
> **Ux64 said:**
> Yeah. But it naturally shouldn't take whole OS with it. ;) It sounds more like one rival operating system. ;)

I didn't mean that the OS crashes. There are many threads about people who don't have 3D enabled going to preview a 3D screensaver and it freezes their display. Then every time they go back to the screensaver preview page their display will freeze before they can change the screensaver. 

I would assume that restarting x would solve the frozen screen problem without rebooting.

---

### Post by zephyrus17 on 2007-12-25
> **Moop said:**
> It could be that you don't have 3D enabled on your video card and any 3D screensaver will crash. Do you have the restricted drivers installed?

It says it's "In Use", but the "Enabled" box isn't ticked.
Problem is,  when I enable it, and restart, it won't boot. (Or maybe it booted, but the screen was blank. There's light, but just blank.)
Then, I'll have to enter Recovery mode, and install the driver from "Envy -t" all over again.

> **Ux64 said:**
> Yeah. But it naturally shouldn't take whole OS with it. ;) It sounds more like one rival operating system. ;)

My VIsta partition being there is causing the crash, you mean?

---

