---
title: "Xubuntu 7.04 - how do I turn off composite from Terminal?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by KiwiPete on 2007-04-27
Hi there

After installing Xubuntu 7.04 I was fooling around with the display settings and thought I'd try turning on "composite" that I'd heard so much about.
Given that my machine is old (Celeron 466 processor, 256 Mb RAM, Intel 810 chipset graphic card) this was a big mistake.
My system obviously cannot cope. Since then I have no usable GUI - screen is just plain pale blue with mouse cursor - but no icons, menus - nothing! So I have no straightforward way of turning that setting off again. Ctrl-Alt-Backspace throws me out of system (back to login)
I can login to a failsafe terminal session - but have no idea how to turn off the composite setting from terminal.
I'm guessing it will be in a .conf file somewhere, but I'll need to know the path and filename to do that.

Can anyone help me here?

KiwiPete (sent from dual boot Win98)

---

### Post by bmathis on 2007-04-27
you can try change Composite to "0" in your xorg.conf file located in /etc/X11/xorg.conf, just make sure to create a backup before you do anything so you can revert back (to your broken GUI) if it doesnt work.

---

### Post by KiwiPete on 2007-04-27
Thanks for the suggestion bmathis, but I cannot find any reference to 'Composite' in the xorg.cof file.
So I am still stuck.

I have also tried reconfiguring xorg using the command:
sudo dpkg-reconfigure -phigh xserver-xorg
and that seems to reset the file back to its original condition.
But the problem (no usable GUI) remains.

One point of interest is that (after logging into the system and getting to the plain pale blue screen with mouse cursor but nothing else) when I press Ctrl-Alt-Backspace to exit I get a fleeting glimpse of the desktop before it all vanishes and I'm back at the login screen again.

Any other ideas / help welcome!

KiwiPete

---

### Post by terranghost on 2007-06-09
I'm stuck with the same problem :@ Any help would be appreciated, i know nothing about debian or ubuntu. 

Xorg.conf doesn't mention "compositing".

OS: Xubuntu 7.04/3rd day using it.
Machine: IBM Thinkpad 600e

---

### Post by terranghost on 2007-06-09
Solution from [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) didn't work for me. :(

---

### Post by Rob-e on 2007-06-14
> **terranghost said:**
> Solution from [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) didn't work for me. :(

this worked for me, i had to add
> Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
to /etc/X11/xorg.conf

which i had to open in mousepad with 
> gksu mousepad /etc/X11/xorg.conf

---

### Post by hencke on 2008-02-19
Thanks Rob-e, editing xorg.conf as you suggested also solved my issues with my ThinkPad 240.

---

