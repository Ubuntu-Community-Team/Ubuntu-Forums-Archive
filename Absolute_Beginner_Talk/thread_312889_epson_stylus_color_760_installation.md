---
title: "epson stylus color 760 installation"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by siman on 2006-12-05
i'm creating this thread for a (female!) friend of mine:

with my help over phone, she tried installing this epson printer with the usual system->administration->printer->new printer procedure. THe wizard didn't recognize the printer, so we manually chose the right model - it was in the list.

But in step 2 it asks for a "ppd" file, and I've no idea what the wizard wants.

Maybe my friend just handled the wizard wrong? Any help would be great... i'm creating her ubuntuforums-account right now, so she'll be able to furhter describe to problem to you in this thread.

---

### Post by larentia on 2006-12-05
yey, this "female friend" is me... please help fast, I need to print a lot of pages for a university project

yours
 larentia

---

### Post by Sef on 2006-12-05
Read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_760"). 

A part of what it says about the Stylus Color 760:

> Note that you *MUST* turn off the so-called "D4" mode of the parallel interface of this printer in order to get it to work. To turn off the D4 mode, follow these instructions (from [http://files.support.epson.com/pdf/sc760_/sc760_f1.txt):](http://files.support.epson.com/pdf/sc760_/sc760_f1.txt):)

Turn on the printer while holding down the Cleaning button (under the inkdrop icons) The paper-out light (under the "paper" icons) will start blinking. Release the Cleaning button and *IMMEDIATELY* press and hold the Load/Eject button (under the "paper" icon) and hold it for about 20 seconds. The Paper Out, Color Ink Out, and Black Ink Out LEDs will light. Release the Load/Eject button. Press the Cleaning Button until the Black Ink Out LED lights. This means D4 mode is off. Press the Load/Eject button and you're done. 

---

### Post by steve.horsley on 2006-12-05
It's a bit confusing, but when you get to step 2:Driver, it is not necessarily asking for a PPD file. It is suggesting a driver, and giving you the option of specifying a custom driver instead. Don't click the button to install a driver - you don't have one. Just click Forward to accept the suggested and recommended one.

That wizard could really use re-wording.

---

### Post by larentia on 2006-12-05
hey,
thxs so much for helping me....well, believe it or not, I DID IT! I fixed this printerproblem all by myself (and because my dear friend refused to help me out!)

yours
liz (the female friend *ggg*)

---

