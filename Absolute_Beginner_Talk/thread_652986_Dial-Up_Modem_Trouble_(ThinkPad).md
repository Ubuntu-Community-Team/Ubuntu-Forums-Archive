---
title: "Dial-Up Modem Trouble (ThinkPad)"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by hilaryp on 2007-12-29
If WvDial will not run, and if your modem is not recognized on a ThinkPad (R61 series), is there any command line editing an absolute Linux beginner can do to use a dial-up connection?

I get "Sorry, no modem was detected!  Is it in use by another program?  Did you configure it properly with setserial?" when I run the /etc/wvdial.conf command.

I first tried to use the graphical set-up (I received my Ubuntu CD just this past month, so I assume it's Gutsy Gibbon...?).  I entered all the Modem information per the instructions, and the DNS information, but apparently IBM/Lenovo modems aren't detected.  If it matters, the chipset is Intel Mobile GM 965.

I downloaded ScanModem but do not understand what to do with the copious amount of commands and/or text generated.  Thank you.

---

### Post by Mark_in_Hollywood on 2007-12-29
It may be that your modem is a "Win Modem". There are drivers in Linux now for WinModems, but you will have to find whether yours is an HSF or HCF or similar acronyms. Then you will have to determine if the Lenovo chipset has drivers for it, download them and install them, too.

As for ScanDisk

in a terminal (also called a console), which you find in Applications/Accessories/Terminal (and I suggest right clicking on this and adding it to the panel or desktop)

do

./ScanModem

or whatever is in the folder (I'm having to respond to this from memory of over a year ago)

That program will run and put a file in the folder or maybe on the desktop that will have the HCF or HSF or whatever and other relevant details.

We can go from there.

---

