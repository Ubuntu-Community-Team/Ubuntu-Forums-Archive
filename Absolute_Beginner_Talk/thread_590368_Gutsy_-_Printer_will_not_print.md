---
title: "Gutsy - Printer will not print"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-24
More 'glitches" in Gutsy.

My printer will not print.  Its an HP.  Where is the printer spool?
Is there an enable/disable button somewhere?

Carl

---

### Post by drs305 on 2007-10-24
There have been reports of HP printers not printing in Gutsy (mine among them). Many involved a printer that was seen by the computer but would not print. I was eventually successful by uninstalling and reinstalling the printer via System, Administration, Printing. It took about 4 attempts but finally started working. One thing that was ultimately unnecessary (and unsuccessful) in my case was installing gnome-cups-manager and trying to install it via that app. I tried it but that didn't help and uninstalled it before my eventual success.

My research on this site has not found any definitive fix for this HP problem and at least a couple of posters have submitted a bug report.

Good luck.

---

### Post by cwmoser on 2007-10-24
I too have an HP printer - HP-2420.  What is the app that needs to be removed and reinstalled in Synaptic?

Thanks

Carl



> **drs305 said:**
> There have been reports of HP printers not printing in Gutsy (mine among them). Many involved a printer that was seen by the computer but would not print. I was eventually successful by uninstalling and reinstalling the printer via System, Administration, Printing. It took about 4 attempts but finally started working. One thing that was ultimately unnecessary (and unsuccessful) in my case was installing gnome-cups-manager and trying to install it via that app. I tried it but that didn't help and uninstalled it before my eventual success.

My research on this site has not found any definitive fix for this HP problem and at least a couple of posters have submitted a bug report.

Good luck.

---

### Post by drs305 on 2007-10-24
In my case and in others I read about, the printer was installed and was recognized by the computer. It just would not print. If you go to System, Administration, Printing, the printer was already listed. I would remove it by highlighting it and choosing 'Delete'. I then added it again. Each time when I chose Add Printer, the usb printer was already visible as an option. At some point the printer started working properly. Something must have triggered it - maybe starting the computer with the printer powered up - I never figured it out.

The synaptic program I tried adding but found unnecessary was gnome-cups-manager, which was how printers were added in Feisty and earlier.

---

### Post by HeWhoE on 2007-10-24
With Dapper, Edgy and Feisty, printing to my HP 4250n through a USB cable worked perfectly.  After upgrading to Gutsy, I managed to print one page before the printer was detected as a new printer.  Then, when the new printer settings were automatically set, printing stopped working.  I've tried drs305's method of uninstalling and reinstalling the printer, but to no avail.

---

### Post by HeWhoE on 2007-10-24
> I just tested a Xerox Phaser 5400 that worked perfectly under Edgy and Feisty.  It's not even detected anymore!  When I try to print using the settings that were carried over from my Feisty installation, it complains, "Not connected?" and says the printer "may not be connected."  When I try to reinstall the printer, it doesn't detect a printer connected through my USB cable.

Nevermind.  The USB port on the Xerox printer is screwy.  I plugged my laptop into another Xerox Phaser 5400 and Gutsy automatically installed the correct driver, and printing to the Phaser 5400 works just fine.  Yay.  By the way, I also followed drs305's suggestions last night before trying to print.  I don't know if that had anything to do with being able to successfully send out a print job this morning.  Thanks, drs305.

---

### Post by drs305 on 2007-10-24
cwmoser,

I've done some searching and several people have had success getting their HPs to work by running the following. It was reported for Kubuntu:

```
sudo /etc/init.d/appamor stop
```

If that works, to make it permanent, make a backup and then edit:

```

sudo cp /etc/apparmor.d/usr.sbin.cupsd /etc/apparmor.d/usr.sbin.cupsd.bak
gksudo gedit /etc/apparmor.d/usr.sbin.cupsd

```

and add this line at the end:

```
/etc/* r,
```

Since mine is now working, I can't try it. Let us know if it works for you.

Referencing: [https://bugs.launchpad.net/ubuntu/+bug/133982](https://bugs.launchpad.net/ubuntu/+bug/133982)

---

### Post by cwmoser on 2007-10-25
I tried:

sudo /etc/init.d/apparmor stop

and my HP 2420 Printer still will not print.

After stopping apparmor, I also tried:

-  removing the USB cable and then connecting back
-  removing the HP 2420 printer in System -> Administration -> Printing and reinstalling.

Still Gutsy will not print.

Carl

---

### Post by philinux on 2007-10-25
Just managed to get a print selection printed by deleting the printer entries and installing again but I get two configuration windows at the same time one gnome-cups and the other a gui autodetect !

Anyway the print of a selection of this page has the header 

"Gutsy - printer will not print" printed on the first line :confused:

Its an Epson r200 by the way

[Edit] Synaptic still had the gnome -cups-manager, the upgrade to Gutsy did not get rid of it. I just uninstalled it now.

---

### Post by HeWhoE on 2007-10-25
philinux, the first line in your printout is the title of webpage you printed.  Maybe your browser sends the title to the output even if you're printing only a selected portion of the page.

---

### Post by philinux on 2007-10-25
Yep I guessed that.

I've reported the gnome-cups-manager being left in synaptic as a bug.

---

