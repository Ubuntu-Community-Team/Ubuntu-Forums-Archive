---
title: "Printer/File Sharing"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Thrender on 2008-03-05
I am pretty new to Ubuntu....I have been using Gutsy on my desktop for about 6 months now...

I recently acquired a laptop and quickly installed Gutsy on that as well...

What I'm looking to do is access my external hard drive and printer (both connected to my desktop) from my laptop which is connected via a wireless router...

I have searched here and found a couple threads about doing just this same thing using ssh and nfs, but don't really follow everything being said...it seems like they're jumping in in the middle or something...I don't know what IP adresses to put in where...Some say to change the desktop to a Static IP, but when I do that I can no longer connect to the internet...

Is there a simple walk-through on this somewhere??  Something for absolute morons that will say go here, click this, etc.

Just for clarification:  I would like to have the external hard drive mounted onto the desktop of my laptop the same as it is on my desktop computer...

Sorry if this is a duplicate thread, but all others seem to be over my head...

---

### Post by stchman on 2008-03-05
> **Thrender said:**
> I am pretty new to Ubuntu....I have been using Gutsy on my desktop for about 6 months now...

I recently acquired a laptop and quickly installed Gutsy on that as well...

What I'm looking to do is access my external hard drive and printer (both connected to my desktop) from my laptop which is connected via a wireless router...

I have searched here and found a couple threads about doing just this same thing using ssh and nfs, but don't really follow everything being said...it seems like they're jumping in in the middle or something...I don't know what IP adresses to put in where...Some say to change the desktop to a Static IP, but when I do that I can no longer connect to the internet...

Is there a simple walk-through on this somewhere??  Something for absolute morons that will say go here, click this, etc.

Just for clarification:  I would like to have the external hard drive mounted onto the desktop of my laptop the same as it is on my desktop computer...

Sorry if this is a duplicate thread, but all others seem to be over my head...

Printer sharing in Ubuntu is a snap.  I have a tutorial for doing it in Feisty but should work in Gutsy.

[http://www.stchman.com/share_printer.html](http://www.stchman.com/share_printer.html)

Sharing files in Ubuntu can be a PITA.  You can either use Samba or NFS.  Both are a pain to configure.

---

### Post by Thrender on 2008-03-06
I appreciate the help stchman, but your guide says that I should set my host to a static IP address...when I do this I lose my connection...is there something I have to do before/after going into Network and switching to a static IP??

---

### Post by stchman on 2008-03-06
> **Thrender said:**
> I appreciate the help stchman, but your guide says that I should set my host to a static IP address...when I do this I lose my connection...is there something I have to do before/after going into Network and switching to a static IP??

The reason for the static IP is that your router may assign you another IP and the printer mapping wont work anymore.

you need to specify a static IP preferably outside your router's DHCP
subnet mask should be 255.255.255.0
Gateway is your router's IP address e.g.192.168.1.1

---

