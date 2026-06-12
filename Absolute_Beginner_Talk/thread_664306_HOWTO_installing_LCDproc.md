---
title: "HOWTO: installing LCDproc"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by firestorm_v1 on 2008-01-11
I'm going to post this here because I don't know where it should go.  Mods, please feel free to move if necessary.


How to install LCDproc on Dapper without pulling out your hair!

Prerequisites:
- Ubuntu computer with an available parallel port.
- HD44780 LCD
- a 6 pack of beer for the celebration (hopefully)

Foreword:
I have several windows servers and I am in the process of moving them to Ubuntu or other linux distros and wanted to keep my parallel port LCD displays operational.  Under windows I was running a program called LCDsmartie which I highly recommend for those of you still on the MS platform. What seemed like a good 2 hours of rifling through configs that didn't work and dodgy help files that were the wrong version, I finally got to the point where by some order of magic, got the display working.  This document will provide a decent guide on installing the LCDproc package and doing some base configuration for getting your LCD working in Linux.

Why:
Why not?  Seriously though, it's a pain in the rear end to write a custom PHP script to poll SNMP information when you just want to make sure the box is alive, or want to see at a glance what the uptime is.  I went from one display to several in a matter of weeks once I found out how nice it was to just look at a little display and instantly see that the computer hadn't crashed or the disks weren't full.  (especially on windows boxes)  If for some reason, the machine hard freezes, the LCD will stop moving, giving a clear indication that something bad happened. 

Starting off:
First off, this document assumes that you have a parallel port LCD display that is already connected.  Unfortunately I don't have a wiring schematic but google has these in spades.  Wiring can be a pain, but make sure you have everything working before you start and this will ensure an easy installation.  Heck, Use LCDsmartie to test your LCD before moving on to this to ensure that it operates correctly and you've already ruled out one of the most common issues with installing parallel port LCDs period.

With that said, let's get started.   For the purposes of clarity, I will assume that the parallel port is at 0x378.  If you're unsure, check your BIOS.

LCDproc is actually two applications, a server (LCDd) and a client (lcdproc).  This guide will walk you through setting up both.

Start off by installing the main package:
(as root)# apt-get install lcdproc
(as root)edit the /etc/LCDd.conf file as shown below:

-Find the line that says Driver=none and put a '#' in front of it.
-Find the line that says #Driver=curses and remove the '#'.
-Make sure all other Driver statements have a '#' in front of them.
-Scroll down until you get to the HD44780 section or type "/HD44780" and hit return.  (VI shortcuts rock)
-Make sure that Port= the I/O port of your parallel port, the 0x is important!
-If your LCD is hooked up and works with LCDSmartie, you will want ConnectionType=winamp
-Some LCDs require an entry here that says 'Charmap=ea_ks0073'  Enter it here but remember it incase it doesn't work.
-My LCD didn't have a keypad or backlight so I left both of these options = no.
-Set the size of the display in WxL format, that is if you have a 20 character wide display that has 4 lines, then you will put 20x4.  If it's a 16 character with 2 lines then set it to 16x2 and so on...
-Make sure the vspan is commented out.  I couldn't test this.
-Make sure that extended=no  I am only running one LCD and have never seen more than one on a parallel port.
-On the DelayMulti option, leave it commented out for now, but if you notice that your LCD can't keep up with the redraw of the LCD program, uncomment this and play with the number until you find one that works for you.
-Uncomment DelayBus=false unless you notice your LCD acting weird or not catching all the characters on the display.
- Save the file and exit ([ESC]:wq)

After the config is saved, run #/etc/init.d/LCDd start  and you should see a display that says LCDproc Server 0 clients, 0 screens on your LCD.  

You're halfway there if all went well now.  For some odd reason, the lcdproc daemon wasn't installed.  I had to get it out of /usr/share/doc/lcdproc/examples.

(as root)cd /usr/share/doc/lcdproc/examples
(as root)gunzip lcdproc.gz
(as root)chmod +x lcdproc
(as root)cp lcdproc /usr/sbin   <--- Remember where you copied it to, you will need this later!

(as root)lcdproc -?
This command will show you all the various options you can add to the display.    For my test, I use C M D X which shows me CPU, Memory, Disk usage and X-load averages.
(as root) cd /etc/init.d
(as root)cp LCDd lcdproc  <------There was no LCDproc daemon script, because it was meant to be run from userspace which is quite annoying. Reboot the box, lose your display?

(as root) vi lcdproc
This is the startup script for the lcdproc client application. Edit as follows:
DAEMON=/usr/sbin/lcdproc  <--------- Remember that path where you copied lcdproc? This is where you need it.
NAME=lcdproc
DESC=lcdproc
DESC="LCDproc local client" 
DAEMON OPTS=" C M D X"  (note the space after the first " and each screen option is seperated by a single space)

Save and exit

(as root)ln -s /etc/init.d/lcdproc /etc/rc2.d/S21lcdproc   <-----------Adds it to the init scripts in runlevel 2 (default) so that it starts after LCDd

Now making sure that your LCD display is still showing "LCDproc Server" go ahead and do the following command:
(as root) /etc/init.d/lcdproc start
You will see a message on the console that says "Starting LCDproc Local Client: lcdproc" and it will return you to the command line.  Now your LCD should be displaying more than just the server screen!

To test, simply reboot the box.  If your LCD screen shows the server message, check the /etc/rcX.d folder and make sure that S21lcdproc is there.  That is how the system calls the script to start and stop when you switch runlevels.

Common Issues:
If your LCD display shows a single bar across the top, it was not initialized properly by LCDd.  Check your wiring and make sure something's not shorted out.  Additionally, if you get garbage on your screen, check to make sure some of the data pins aren't shorted to each other as this will also muck up things.   If all else fails, edit /etc/LCDd.conf and comment out the "Charmap=" line we put under the HD44780 section mentioned above.

If it still doesn't work and you have a windows box with a parallel port handy, try using LCDSmartie on it with your display and see if it works there.  If not, then it's definately a wiring or LCD problem.

I will warn you, I am by no means an authority on LCDs or interfacing them to computers.  I didn't write the LCDproc applications nor do I want to take credit for any of it.  I am merely sharing my experience so that someone else doesn't blow 2 hours and 3 cigarettes trying to get it working.  I have not tried any LCDs other than the one described here so unfortunately I can't offer any additional assistance other than this howto.

Now if all that's working, crack open a cold one, you've earned it!

Good luck!

---

### Post by SOULRiDER on 2008-01-12
You should ask a mod to move this to the Tutorials and Tips section, its better off there.

---

### Post by seanmheff on 2008-06-11
Thanks for this guide. It helped me alot!

---

