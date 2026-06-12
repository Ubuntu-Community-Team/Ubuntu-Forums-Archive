---
title: "The usual mouse scroll problem with a twist,"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by sms001 on 2007-06-18
Good day and thanks in advance for any help I may receive.


Today's Problem:

Non-scrolling wheel mouse.
Logitech MX cordless optical PS/2 clicking wheel mouse ON A KVM SWITCH.

I originally installed Dapper to avail myself of the Long Term Support.  Because of a variety of hardware problems, I moved on to Feisty. (Clean Install)  Feisty solved today's problem right out of the box - the scroll button on my mouse was not scrolling in ANY application.  Then it stopped. (After a cluster of Update Manager updates.) I overwrote the "/etc/X11/xorg.conf" with the one originally generated during my install - no go.  I followed several online methods for correcting this problem.  What finally did the trick was Matti Kurkela's suggestion that the fault lay with the KVM switch, not the mouse:
	
	* Look for the line reading "parm: resetafter:Reset(...)". You can set this and the other parameters 		        by editing the /etc/modprobe.d/options file. The resetafter parameter tells the mouse driver how many 		        bad packets are accepted before the mouse is told again which protocol to use. In this case you want 		to change that from the default (= never) behavior. So edit the options file: 

        gksudo gedit /etc/modprobe.d/options

    	* Add the following line: 

     	options psmouse resetafter=1

    	* Save and exit. You can now restart the mousedriver for the changes to take effect: 

      	sudo modprobe -r psmouse
      	sudo modprobe psmouse

This worked like a charm - until I switched machines and then back. Then I had to drop to terminal and renter the two modprobe commands to reset.  

My question (finally!) is this: Is there a more elegant solution to this problem? I realize that as I use the linux machine more and more switching back and forth won't occur as often, but in the meantime I'd like to find a way to do this automatically.











___________________________________________________________


[email]newbuntu@s112200228.onlinehome.us[/email]

To avoid retyping I've created a template.  My "Problem of the day" will be followed by a cut and pasted synopsis. It is the full problem list, hardware list, and software list.


Backstory: Twenty-four years PC experience including Macs, clones and some dabbling in Red Hat, SuSe and now Ubuntu.

Currently: Trying to establish a rock solid enough Linux platform to relegate the Windows machine to the background.




Problem List:

Mouse
Drag and Drop:
	urls from address bar to desktop do not reopen with Firefox
	[.desktop extension? sometimes d'n'd shows "+" (copy) and that 
	bounces back to the address bar.  sometimes shows "?" and that seems to 
	copy.
	gedit text file on desktop cannot be dragged into open gedit window
	themes - sometimes error message, sometimes says Installed but does not appear

Searching:
	Default to File System
	Search for single file types
Sound:

Installing:
	d/l and install with Synaptic doesn't always result in addition to Applications Menu either shown or 		        not.
	Alacarte doesn't have all executables as options

File System:
	In general, what is stored where

Startup Items:
	What gets run at start and what are the differences

Evolution:
	How to move "Contacts" to "Address Book"

Machine:

HP 8560C
System BIOS Version: PTLTD  - 6040000 Date: 05/24/99
CPU: Intel Celeron 500MHz (Mendocino) stepping 05 
Physical Memory: 255 MB 
Display Adapter: Intel 82810 Graphics Controller

DVD/CD-Rom: Teac CD-532E-B /SONY CRX230EE

ATAPI: Intel 82801AA Bus Master IDE Contrller

Modem: HCF 56k PCI Modem

NIC: HP EN1207D-TX PCI 10/100 Fast Ethernet Adapter

PCI Slot 2 (PCI bus 1, device 9, function 0)

Audio: Riptide
Keyboard: HP Multimedia SK 2505
Mouse: Logitech MX Cordless Optical Mouse 
(I realize this machine is pretty weak, but free is free.)

Software:

Linux version 2.6.20-16-generic
Ubuntu 2.6.20-16.28-generic

---

### Post by sickpuppet on 2007-06-18
Hi sms001 - 

(Your goal is adminarable - replacing Windows completely - mine's the same. So far Ubuntu is looking like an excellent candidate - best Linux I've tried so far, but not without its glitches.)

To answer your question - or rather, to suggest an alternative solution:

You could ditch the KVM! If you only have two boxes plugged into it and you have room on your desk for another monitor, then a very elegant solution is to use [Synergy2]("hhttp://synergy2.sourceforge.net/").  It's a sourceforge project, so it's kosher/halal free software. Synergy lets you share a single mouse and keyboard between two boxes - just plug a monitor into each one and synergy takes care of moving the mouse between the two screens.

I've been using Synergy for about two years at work (Fedora Core and Windows 2000), and it works a treat, apart from occasional funkiness with copy and paste (I have no affiation or interest in the Synergy project - I'm just a happy user.)

cheers
Ben

---

### Post by sms001 on 2007-06-23
sms> My question (finally!) is this: Is there a more elegant solution to this problem? I realize that as I use the linux 
sms> machine more and more switching back and forth won't occur as often, but in the meantime I'd like to find 
sms> a way to do this automatically.

sickpuppet> You could ditch the KVM! If you only have two boxes plugged into it and you have room on your
sickpuppet> desk for another monitor, then a very elegant solution is to use Synergy2. It's a sourceforge 
sickpuppet> project, so it's kosher/halal free software. Synergy lets you share a single mouse and keyboard 
sickpuppet> between two boxes - just plug a monitor into each one and synergy takes care of moving the sickpuppet> mouse between the two

Thanks!  I will certainly look into Synergy [[http://synergy2.sourceforge.net/]](http://synergy2.sourceforge.net/]) when a little more desktop real estate develops. The cut'n'paste aspect is a real draw - network imming or saving to a shared folder then switching then opening is an occasional hassle. For right now I guess I'll settle for my little terminal hack.  It discourages me from leaving Linux anyway, so there is a silver lining :)

---

