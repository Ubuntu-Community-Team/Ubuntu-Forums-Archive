---
title: "[SOLVED] MAC PPC - GDM will not Start - Kubuntu LIVE CD"
date: 2007-10-19
forum: Apple PPC Users
---

### Post by mel_phil@flashmail.com on 2007-10-19
Hi 

Have used Kubuntu on various Intel based machines with great success & very little hassles. Have tried to load it onto my G3 Imac & had huge issues. I have wasted that much time & effort reading & trying things it is time to either scrap the idea or get some help from someone more experienced with Linux/MAC. So here the story goes

THE PROBLEM:
I wish to run the LIVE CD on this IMAC. The problem is I cannot get gdm to start

I get the CD to boot OK, I can edit the xorg.conf file to change the HorizSync/VertRefresh/default refresh  rates & # out the "Load DRI". VI tells me the changes have been saved (No problem there). 

Everything is rosy until I try to restart GDM. I type the command sudo /etc/init.d/gdm restart. It just comes up with "Command not Found". I have tried to Kill gdm and it says "No process killed"  implicating it has not been started or maybe even not there. I have gone through the directory folders & cannot even see any files that have a gdm reference in the init.d folder

I have looked at lots & lots of websites for this problem & have tried various alternate versions of the above command that have worked for other people. eg sudo /etc/init-d/gdm start etc - All to the same result "Command not Found"  

Also tried startx and I get error message "Fatal Server Error: Server is already active for display 0 if this server is no longer running remove /tmp/.X0-lock and start again"


THE HARDWARE:

IMAC Indigo G3 @ 350 Mhz (Slot Loading)
256 RAM
8 GIG Hard Drive
Firmware Update 4.19 
OS 9.1 is installed on the Hard Disk

The only problem I have with the IMAC is that the onboard Ethernet card no longer works. But this should not be a problem because I have installed & and run Kubuntu on a Intel PC with a non functioning NIC without a problem.


KUBUNTU Version Info

"kubuntu-6.06.1-desktop-powerpc.iso" 

was downloaded from the KUBUNTU site through the optus Net mirror Australia. It was downloaded & burned on a Windows PC using Nero 7. This should not be a problem as I have always got my MAC & Linux software this way without problem before.

I did read on some sites it can be burn problem, However I have tried to burn it on 2 different PC's with 2 different Writers, different burning software different & brand disks 1 burned at at 48X & the other at 4X and still the same result. The CD is readable in OS9 no problems

I have never any problems running Linux/Intel combinations before. I even get a MAC OS whatever to play ball with everything I want it to do, but this Linux/MAC combo has me stumped.


Any help would be greatly appreciated, and I hope it is something really stupid I am doing so its an easy fix.


Many thanks in advance 



P

---

### Post by kugn on 2007-10-20
Er, why do you use GDM on a Kubuntu disc? KDE has its own KDM?

---

### Post by mel_phil@flashmail.com on 2007-10-20
Many Thanks for the reply your help is appreciated. What would I use in place of gdm then? Sorry for being stupid!

---

### Post by kugn on 2007-10-20
I'm really not an expert. But I think KDM is the counterpart to GDM on KDE. So instead of /etc/init.d/gdm, try /etc/init.d/kdm

Hope it helps. :)

---

### Post by mel_phil@flashmail.com on 2007-10-20
Sounds pretty obvious I'm sorry K instead if G?

1 embarrassed goose!

---

### Post by mel_phil@flashmail.com on 2007-10-20
Thank You very much Kugn solved my problem!!!

---

