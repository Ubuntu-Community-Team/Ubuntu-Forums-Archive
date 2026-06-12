---
title: "Broadcom Wifi Graphical installation"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by jmills on 2006-01-10
I'm kind of an amateur; so, I could get this wrong.  However, after mucking around for a while, here's how I got my HP laptop running a broadcom wifi card using ubuntu's graphical interface only.  (No command line instructions.)

First: Click on “System – Administration – Synaptic Package Manager”

You'll need to enter your password.  

Top right hand of the Synaptic Package Manger, click on “Search”

In the Search box, type in “ndis”

There are three “ndis” files that are available.  They are: “ndisgtk,” “ndiswrapper-source,” and “ndiswrapper-utils”  Mark all three for installation.  Then click on “apply” to install the three packages.

“ndisgtk” is the graphical interface for updating your wifi driver.  Once "ndisgtk" is installed, click on System – Administration  and you'll see at the bottom a new icon called “Windows Wireless Drivers”  

When you click on the “Windows Wireless Drivers” you will see a box allowing you to “Install New Driver”  Click that icon and you'll get a box asking for location of the driver.

Now you have a tricky problem.  How to get the Windows XP driver?  The Broadcom driver called bcmwl5.inf

To get it, I simply used a Windows XP machine, went to HP and downloaded the executable file for the broadcom wifi card.  Then I double clicked the “.exe” file and installed the driver on my windows machine.  From HP, my broadcom driver is SP2837.exe  

The executable file puts a folder on your Windows C drive and inserts the .inf file (driver) in that folder.   Either email that to your linux machine, or link up linux and windows machines with Samba.  Anyway, you need to copy the bcmwl5.inf file to a location on your ubuntu machine.

Then, using the “Install new Driver” on the “Windows Wireless Drivers” box, just click to install the bcmwl5.inf file.

Then you can configure the network by identifying a WEP key (if you have one).  (Unbuntu should automatically call up the network ID).  

Problems?  Try clicking on the dual monitor icon at the top right hand of your ubuntu desktop.  You may need to check under "name" and see that wlan0 is active.

Restart the computer.

Anyway, it's possible to get even a broadcom internal wifi working without ever opening a "terminal" window and without ever typing in any command line text.

Away you go.

---

