---
title: "How to setup a printer...?"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by TheShadow99 on 2007-04-03
I know setting up a printer is supposed to be easy, but so far I'm having no luck with it...

I have pretty much 4 different ways I connect to printers here: direct via parallel cable (old HP 670C's), direct via usb (newer HP Deskjets), Via redirection from a windows 2003 server (they are 'shared' from it, but are really HP jetdirect boxes scattered around in various places), Or over the network by a HP Jetdirect box.

So far I can't get any of those four options to work on any of the ubuntu/edubuntu installs we have here...

Both types of direct connections fail to find a printer of any sort during startup and manually selecting options for the printer does not work. This is true no matter if I use 'HP_undetected_printer' or 'LPT1' for parallel ones.

Network printing is worse in a way, because I select the correct options (in fact it seems to see the printers just fine), but fails to print anything...

I need some help from someone who has a better idea what's wrong than me...

---

### Post by jhenager on 2007-04-03
Check out HP's site for HPLIP (HP Linux Imaging and Printing). Their support for Linux is very good. I found that setting a static IP address on the printer(s) is the best way to go. The installer software takes a long time to load, and it didn't automatically find my printer, but I selected the manual option and input 192.168.2.37 and bam! I was there.
[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)
HPLIP Self Extracting Archive With Installer

This is an experimental release that packages a self-extracting installer together with the regular tarball. The self installer is know to work on the following distributions (see note 2):

    * SUSE Linux (10.0, 10.1, 10.2)
    * Fedora (3.0, 4.0, 5.0, 5.92, 6, 6.0)
    * PCLinuxOS (2006.0)
    * Ubuntu (5.04, 5.1, **6.06, 6.10**, 7.04)
    * Debian (2.2, 3.0, 3.1)
    * Mepis (6.0)
    * Mandriva Linux (2006.0, 2007.0)

To use the self-extracting file, follow these steps:

   1. Download the file to a convenient location (e.g., home directory or desktop, etc).
   2. Open a console/terminal and cd to the download directory.
   3. Type in and run this command: 'sh hplip-1.7.3.run'

I didn't realize it was experimental - it works ok on my system.
Note: you probably want to run '_sudo_ sh hplip-1.7.3.run'.

---

### Post by TheShadow99 on 2007-04-03
Well I ran hplip and I get stuck on a part that says 'postfix configuration' and displays a list of options regarding email (or so it would seem) with an 'ok' button on the bottom of the xterm... except it doesn't let me select 'ok'... hitting escape lets me get to another menu to select one of five choices (those from the list), but selecting any of them (by hitting enter over one) sends me back to the information screen...

I can't seem to leave this part at all... So what am I supposed to do...? :(

---

### Post by 11hjpphty76lkjj on 2007-04-03
Please look at this doc:

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

I've recently updated the instructions to include how to complete the postfix install.

A

---

### Post by TheShadow99 on 2007-04-04
Sigh... tab is the only key I didn't try...

Oh well... A few machines still have issues, but those are due to the filtering done here (that I can't bypass in linux), which ended up causing all sorts of issues with the MSfonts that some wanted installed... And which can't be because the filter kills all downloads with a .exe extension... That is out of my control even if I am the network admin, because the school has the ISP do that for them and that was done before I started...


Thanks for your help.

---

