---
title: "HP Deskjet 3420 Printing Problem??"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by KeyboardJockey on 2006-04-16
First of all many thanks to all those forum members who have helped me get my Ubuntu 5.10 up and running.

It does everything I want it to do now -- except print,](*,) 

I've tried everything I can think of to cure the problem which is the document is sent to the printer the head moves backwards and forwards in the same pattern as if it was printing a document but the paper remains stubbornly blank.  It is not an ink or a hardware problem as I booted up my windows partion and the printer works fine from the win xp partition when I installed the driver.

However it refuses to print in Ubuntu.  

I've tried removing the printer and reinstalling it using system-printing-add/remove printers, I've tried going into synaptic and re installing the hpjis driver but it still won't print.  

I'm wondering if I'm overlooking something very simple here.

I'd be grateful for any suggestions on this conundrum.

thanks

---

### Post by uteck on 2006-04-16
What type of printer is it?  If it is an HP, make sure the hpijs, hpoj, and foomatic-db-hpijs packages are installed.

---

### Post by KeyboardJockey on 2006-04-16
Thanks Utek

It is an HP Deskjet 3420.  I'll pop into Synaptic and install those packages.

---

### Post by KeyboardJockey on 2006-04-16
Nope -- tried this and it still feeds out a sheet of blank paper even though there is ink in the cartridge as it prints OK in WinXP.

---

### Post by tassou on 2006-04-17
Hi KeyboardJockey,

same problem here on a 3425, blank page, nothing on it, although the printer acts as if it was printing. By the way, it seems that the "hpijs" driver is used and not the "hplip", so it does not appear in hp-toolbox control.
The black cartidge is brand new and I managed to print a black page flawlessly using the official HP driver on windows xp.
 Please post back any solution, I keep investigating around it.

Regards

---

### Post by tassou on 2006-05-05
Hello there, 
this problem is still not solved. Anyone had this strange experience and solved it ? Please post anything you would think might helps. 
Thanks

paul

---

### Post by darv on 2006-05-29
I'm having the same problem but I've found something else out that maybe you guys could look into.

If I print anything, black or colour, no matter what settings i'm using (even trying to force it to use the black cartridge) ubuntu always uses the colour cartridge to print. This is OK, but colour cartridges are expensive.

I discovered this because I noticed the printer was printing much slower than in windows, and when i took the colour cartridge out, the page comes out blank.

Any ideas on why it won't use the black cartridge?

---

### Post by az on 2006-05-29
[QUOTE=darv]
Any ideas on why it won't use the black cartridge?[/QUOTE]
Does it do the same thing in Dapper?  Can you change the printer default ink properties to just print greyscale?

---

### Post by linmick on 2006-07-12
The reason for the troubles is listed here: [https://launchpad.net/distros/ubuntu/+source/hplip/+bug/23099](https://launchpad.net/distros/ubuntu/+source/hplip/+bug/23099) (however noone was able to fix it so far) The problem is known your likely out of the color ink. Since it never switched to black anyway! Good luck in fixing your problem and share here if you find a solution. :)

---

### Post by hickmann on 2006-09-15
Interesting, I have this same problem and am actually without color ink. In the link linmick posted, it has been reported as a bug, but they didn't discuss this problem anymore since last june. Did anybody find a solution since then?

---

