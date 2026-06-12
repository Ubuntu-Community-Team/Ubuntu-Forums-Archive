---
title: "Trouble installing Ubuntu"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Bob Tomas on 2007-09-13
I am attempting to install Ubuntu 7.04 on an IBM Model 8306 computer with a View Sonic VA703 LCD monitor. The machine 

contains an Intel 82845G video chipset and 512 MB of memory. When I first attempted to run DVD to get the OS on as a trial, 

the setup text was large meaning that the screen resolution was working as VGA. I restarted the disc and when the Ubuntu 

flash screen came on I pressed F4 and adjusted the screen resolution to 640x480x16. The setup went through the sequences and 

it ended with a black screen and a message "Out of Range" and the Ubuntu musical intro.

I then attempted to install Ubuntu using the alternate CD. A message came up indicating that the Gnome was not installed 

because of missing software. I ran the sudo command to reconfigure the xserver per the instructions in the Ubuntu instruction 

manuals and got the same results. I uninstalled the Ubuntu by clearing the MBR and deleting the Linux partitions taht were 

set up during the installation.

I have two other computers in my LAN so I decided to see what results I would get. The results follow:

Machine 2: A 980 Mhz machine with  an ATI Radion 9550/X1050 adapter operationg into Hanns-G HW 173D LCD monitor. It contains 

384 MB of memory. On boot-up, the Ubuntu splash screen came up and I opted for the operate from CD option. The start-up 

sequences went through, the Ubuntu system started with a screen resolution much higher than I expected. I chose a different 

screen resolution which was put on and the system did all functions as allowed.

machine3: an IBM model 8305 with the Intel 82845G video chipset working into OptiQuest Q7 monitor. I had to adjust the screen 

resolution to 640x480x16 using the F4 key on the splash screen before opting for the trial mode. The setup went through the 

entire sequence bring up the Desktop screen. However, I was not allowed to change the screen resolution as I could on Machine 

2.

Windows XP Home edition is installed on all machines tested.

I have a specific need to install Linux on machine 1. What do I need to do to get it working fully?

---

### Post by ramjet_1953 on 2007-09-13
If you follow this link: [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

It will guide you through almost every install scenario.

Regards,
Roger 8)

---

### Post by Bob Tomas on 2007-09-14
> **ramjet_1953 said:**
> If you follow this link: [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

It will guide you through almost every install scenario.

Regards,
Roger 8)

Tnx for responding. Downloaded entire guide. Searched for material relating to monitors and video cards. Did not find anything related to my problem. Most of the instructions and guides were on Nvidia cards. Closest was a section describing changing screen resolution on Intel 915 chipsets. Chipsets in my computer are Intel 845 series. Tried following instructions for 915 set and was rejected. Anybody else have the same problem?

---

