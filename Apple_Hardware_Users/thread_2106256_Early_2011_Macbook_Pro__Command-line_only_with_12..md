---
title: "Early 2011 Macbook Pro / Command-line only with 12.04 install"
date: 2013-01-18
forum: Apple Hardware Users
---

### Post by NeverConvex on 2013-01-18
I've installed Ubuntu 12.04 (64-bit) on an early 2011 Macbook Pro (hardware version 8,2, according to "sudo dmidecode -s system-product-name" entered at the command-line terminal), intending to dual boot it with OS X Lion, but can't seem to get Ubuntu out of command-line only mode.

The procedure I followed during installation was:

1. Boot into OS X
2. Use disk utility to resize the partition, create bout 250 GB of 'free space'
3. Install Ubuntu 12.04 (64-bit) via LiveUSB, choosing the 'Install alongside OS X' option

General issue: I can only get the installer to operate at all if I use 'e' to edit the boot options and add nomodeset before, after, or in place of 'quiet splash.' Post-install, I also have to use nomodeset on booting; if I don't, then the 5-dots Ubuntu loading screen appears, loads, and immediately thereafter the screen displays a number of graphical errors, e.g. totally black screen with some white-noise lines splayed about the top of the screen.

I'm assuming this is a video drivers issue of some kind; lspci | grep VGA gives:

VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Series]

I've installed/uninstalled/reinstalled the fglrx proprietary drivers using a few different googled guides; with fglrx (I believe) properly installed, and without using nomodeset, I can get past the 5-dots loading screen but then get an 'Operating in Low-graphics Mode' displayed message. Hitting 'Enter' removes that menu; then a 4-option menu is displayed allowing me to choose how I'd like to continue (with the screen black except for this menu), but at this point the computer seems to freeze, or at least I lose keyboard control, as I can't seem to move between the menu options at all.

With or without the fglrx drivers installed, starting the system with 'nomodeset' causes the system to enter command-line mode; I'm prompted for my log-in credentials and can access / use Ubuntu vis-a-vis command line, but I haven't been able to figure out any way to get the usual Ubuntu GUI working.

Additional details---

With fglrx installed, fglrxinfo returns:

Error: unable to open display (null)

Also, on some of my installation/repair attempts, I get 2-3 lines of "b43/ucode29.fw not found" errors and a message indicating that I should download and install the drivers manually, along with an http address; from googling I gather these are wireless drivers. I don't need the wireless to work just yet, as I have a wired connection I can use to perform downloads and such.

Edit # 2:

I've about given up on this for now, just going to suck it up and become accustomed to using OS X on my laptop. Before admitting defeat, though, I noticed on one of the Ubuntu-on-a-Mac installation guides that 12.04 (Precise Pangolin) was not listed as supported for the 8,2 Macbook Pro, so I switched to Oneiric Ocelot instead. On Oneiric, I can install from USB (just as I could with Precise Pangolin), and with both nomodeset and apci=off set as boot options, I can get past the Ubuntu loading screen, but then the O/S hangs at "Checking battery state..." CTRL + ALT + F1 lets me open a text terminal, but attempting to manually start an X Server yields an error ('no screens found,' if I recall correctly). So, in effect I'm stuck with command-line only access to Ubuntu again.

Oh well! Here's to branching out and becoming comfortable with OS X, heh.

---

