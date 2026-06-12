---
title: "VMWare Fusion 10, Ubuntu 16.04 LTS low graphics mode issues"
date: 2018-02-19
forum: Apple Hardware Users
---

### Post by rpg711 on 2018-02-19
[COLOR=#111111][FONT=Ubuntu]**Background**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have Xenial Xerus installed on a Mid-2014 Macbook Pro OSX High Sierra host, running in a VMWare Fusion 10 instance.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]On Fusion 7, I had no issues with Ubuntu on VMWare. However, since I also virtualize my Bootcamp partition for convenience... I was forced to update to 10 since 7 no longer supports loading Bootcamp on the latest OSX.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**VM specs**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]3 Cores, 4GB ram, 20GB HDD (10GB free), Hardware version 14. 768MB VRam[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**Issue**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I just cannot ever restart or shut down the VM. If I restart or shut down Ubuntu, on the next reboot, I get the message: "Sata device 0:1 could not be connected, always try to connect when starting this VM?". Then, Ubuntu starts in low graphics mode, and I am forced to restore a snapshot of my VM when it was working. This is workable, with proper snapshotting and backing up I have been passably using Ubuntu. However, I have had to go into the console in low graphics mode after a crash and back up my work, restore snapshot, and restore my work many, many times. Conceivably if I ever start leaking memory and need to reboot, I'll need to re-image the VM again.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**What I've Tried**[/FONT][/COLOR]

[LIST]
[*][FONT=inherit]Different allocations of ram, cores.[/FONT]
[*][FONT=inherit]Reinstalling x-desktop[/FONT]
[*][FONT=inherit]Reinstalling/updating Nvidia drivers (this broke the hell out of the VM when I tried)[/FONT]
[*][FONT=inherit]Reinstalling VMWare tools[/FONT]
[*][FONT=inherit]Reinstalling Ubuntu.[/FONT]
[*][FONT=inherit]Installing all manner of different desktop environments[/FONT]
[*][FONT=inherit][Pretty much everything in the answers to this question]("https://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error")[/FONT]
[/LIST]

---

