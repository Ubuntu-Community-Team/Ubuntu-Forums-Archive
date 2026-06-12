---
title: "Need help with Printer setup"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by NewJack on 2007-03-18
I am only a week and a half into using Ubuntu (or linux for that matter) and I like it so far, but I have a problem.

I have done some searching here for help before posting this.  I have a Canon S800 printer that I'm trying to setup in Ubuntu Dapper.  I go to Admin> Printing> Add Printer, click on Add Printer  and it shows my printer as local, I click forward it shows my printer on the drivers screen and I click apply. 

 When I go back to the installed printers screen it shows my printer as "Ready".  When I try to print something the out of service light flashes.  I check the paper, nothing.  I check the ink cartridges, nothing.  USB cable is in properly.  

What am I doing wrong (if anything)?  Is there a better way to install this printer?  I also have an HP 1200 LaserJet that I want to install next.  Any recommendations would be greatly appreicated.

Joe

---

### Post by eljalill on 2007-03-19
Note that compatibility varies greatly between manufacturers. As far as I know, HP works best under ubuntu (connecting mine: F380 posed no problem at all, it was basically plug and play...), Canon can be made to work, and Lexmark poses a problem. 
So trying out the HP1200 might be a good option...

---

### Post by lemmy999 on 2007-03-19
linuxprinting.org shows that the S800 only works "partially" under linux. You may want to go to the following page and read more.

> [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-S800](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-S800)

at the least you will need to install the relevant drivers for your printer.

---

### Post by NewJack on 2007-03-19
I know that the S800 isn't the best choice, but unfortunately I can't afford to pick up another color printer at this time.  I just hope to get it working the best I can for now.

I hope that installing the HP LaserJet 1200 goes a bit smoother later tonight.  Now on linuxprinting.org, it recommends the pxlmono driver but should I use HPLIP instead?  Another question is, if I use HPLIP what directory should I install it to?  

Sorry for the n00b questions, but I really like Ubuntu so far and getting my printing stuff straightened out would help.  Thanks!!!

---

### Post by NewJack on 2007-03-20
Ok an update.....

It seems as though my S800 is not an option.  It's a hardware problem and it doesn't print on WinXP either anymore.  I now own a Canon paperweight.

Next, I tried installing my HP LaserJet 1200.  It recommended that I use the pxlmono driver, which I thought I installed correctly.  All seemed to go through ok, but when I print anything, it comes out enlarged.  For instance, if I print from Firefox default start page, it only prints the left side of the page and the fonts look odd.  Did I use a wrong driver?  Is there something I can do or somewhere/how I can adjust the settings to fix that problem?

---

### Post by Sef on 2007-03-20
> Did I use a wrong driver?

No that is the right driver for it.  How did you install it?

---

### Post by NewJack on 2007-03-20
New Printer>Use detected printer (HP 1200)> Driver page came up and on the bottom it showed "pxlmono" as the recommended driver so I clicked on "Install Driver" and pointed it to /usr/share/cups/model where the pxlmono driver was located and clicked OPEN.  Then I finished out the installation.  I forgot to mention in my last post that when I printed a test page, I got the same results as printing from FireFox.

---

### Post by NewJack on 2007-03-22
Bump

---

### Post by 11hjpphty76lkjj on 2007-03-23
Your HP LaserJet 1200 is supported by HPLIP.

Please see: [http://hplip.sourceforge.net](http://hplip.sourceforge.net)

for additional information.

---

### Post by NewJack on 2007-03-25
Thanks alot!  I just installed it and even though during install it said that there were a few .dev files that it couldn't install, it is actually printing correctly.  No more zoomed pages.

Thanks!
Joe

---

