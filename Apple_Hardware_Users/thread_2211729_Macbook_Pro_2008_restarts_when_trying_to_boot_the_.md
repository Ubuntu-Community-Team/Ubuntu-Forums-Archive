---
title: "Macbook Pro 2008 restarts when trying to boot the Ubuntu 12.04 Live CD"
date: 2014-03-17
forum: Apple Hardware Users
---

### Post by Drew_H on 2014-03-17
Hello everyone,

I have been all over the internet trying to come up with a solution to this issue and I probably should have came here first! 
So right now I am in the process of upgrading my office's fleet of old Macbook Pro 2008s from OSX 10.5 (Leopard) to Ubuntu 12.04 LTS and I have ran into a problem, the Live CD refuses to boot completely.  I will get to the menu that asks if I want to "try" or "install" ubuntu, but once I select one of the options It will act like its booting into Ubuntu but will then reboot back to the boot menu or OSX.  But what is really odd is the fact that the Macbook would boot the Live CD a week ago.  So it has to be something I have done right?

Here's the timeline of what I have done so far one of our Macbook Pros to install Ubuntu.

-Booted into the Ubuntu Live CD (last week)
-shutdown computer

-Booted into OSX
-Thawed the Hard Drive in Foronics DeepFreeze
-reboot
-Booted to OSX 10.6 (Snow Leopard) install disc to remove the administrative firmware password set to the computer. (I didn't have the 10.5 disc, but it still worked to remove the firmware pass)
-reboot

-Booted back into OSX
-Installed ReFit Boot Manager
-Cleaned up empty space on hard drive in Disk Utility
-Partitioned the hard drive using Disk Utility
-rebooted

-Booted to Ubuntu Live CD using ReFit
-Loaded to the Try/Install Menu
-Attempted to "try" ubuntu
-Computer acts like it is loading Ubuntu (logo with loading icons below it)
-Computer reboots abruptly
-Computer boots to OSX


WHAT IS GOING ON?!?!

Some other things I've tried are: reburning the ISO to another disc at a slow speed, booting from a Live USB drive, reinstalling ReFit. All to no avail.  But thats the end of my troubleshooting because I really don't know what else to try.  I know that this version of Ubuntu is compatible with this Macbook Pro because I have booted the live CD to the Ubuntu desktop before on it and it ran just fine.


If anyone can shed some light on what I'm missing here that would be greatly appreciated!
Thanks in advance

Drew

---

### Post by PartisanEntity on 2014-03-18
Whenever I have had problems trying to boot a laptop from the Ubuntu live CD, I have tried the alternate install CD. The latter almost always works. Give that a try. (As the name says, the alternate install CD is not a live CD, it will boot straight into the installer).

---

### Post by Drew_H on 2014-03-18
I will try doing that when I go back into work in a few days.  I really appreciate the input, thank you very much!  I actually managed to have some luck booting the Live CD today by setting the acpi=off, and turning on noapic setting in the Additional Options menu.  However the mouse was running a bit buggy, and the Ubuntu OS installer locked up when I tried to install Ubuntu to a partition.

---

### Post by Drew_H on 2014-03-24
Using the alternate install CD worked like a charm!  Thank you very much!

---

### Post by PartisanEntity on 2014-03-24
Glad to hear that and thank you for the feedback, this way others can benefit from your experience :)

Please make sure to mark your thread solved, this helps users looking for solutions to the same problem.

---

### Post by maxbar on 2014-04-02
When going to the Ubuntu download page, there's no link to alternate CD images. At least I couldn't fine one. Would you please be so kind to link to the page with the alternate CD images?

Much appreciated!

---

### Post by PartisanEntity on 2014-04-02
Here you go: [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

They are under the BitTorrent section.

---

