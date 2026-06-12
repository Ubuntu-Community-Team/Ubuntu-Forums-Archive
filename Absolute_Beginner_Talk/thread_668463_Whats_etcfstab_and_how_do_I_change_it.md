---
title: "Whats etc/fstab and how do I change it?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by PeteBeech on 2008-01-15
I've been working through a HOWTO post on installing a Lexmark z600 driver and have reached the final step where typing

$ /usr/lib/cups/backend/z600 

is supposed to produce an output on the screen.

In my case I just get the command prompt and the advice in this event is to "mount the usb filesystem" by adding an entry to my /etc/fstab file.  

I'm quite pleased I got this far by mindlessly copy-typing from the HOWTO instructions but now I seem to have hit the buffers.

Fact is, I have no idea what /etc/fstab does, where it is, how to change it or whether it's safe for someone as ignorant as me to do so.  Do I  even have the right permissions in Xubuntu and how do I get them if I haven't?

Any advice would be welcome.

---

### Post by philinux on 2008-01-15
Can you post a link to the howto.

It might need 

sudo /usr/lib/cups/backend/z600  assuming z600 is an executable fiel.

---

### Post by Aurora@FleetBuzz on 2008-01-15
> Fact is, I have no idea what /etc/fstab does, where it is, how to change it or whether it's safe for someone as ignorant as me to do so. Do I even have the right permissions in Xubuntu and how do I get them if I haven't?
This may help explaining what /etc/fstab is and does.
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by PeteBeech on 2008-01-16
> **philinux said:**
> Can you post a link to the howto.

It might need 

sudo /usr/lib/cups/backend/z600  assuming z600 is an executable fiel.


Thanks for responding.  

The HOWTO is here [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

I won't have access to the PC I'm trying to set up until tomorrow but I'll post a note after that to say how I'm getting on.  Two bits of information that might give a clue to the problem:

1.  The Lexmark works on the same PC (a Compaq N400C notepad) under Windows but only when it's connected through a PCMCIA USB2.0 port adapter - none of the machine's own (USB1) ports will drive the printer.

2.  Under Xubuntu an HP Business Inkjet 1100 plugged into the same PCMCIA USB2.0 port works fine, and I can print a test page with no problems.  I'm guessing this narrows the problem down to the Lexmark driver.

---

### Post by PeteBeech on 2008-01-17
The printer is working! 

In the end I ignored the lack of any output when I entered **/usr/lib/cups/backend/z600** and went ahead anyway and installed the driver in Settings.  I'd done this once before and when I tried to print a test page nothing happened, but this time it printed.

---

