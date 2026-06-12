---
title: "Having Wifi connection on Bodhi 12.04 2.3.0"
date: 2013-06-09
forum: Any Other OS
---

### Post by primitive1 on 2013-06-09
Yes i have been chatting with Bodhi forums and want to see anyone's input on here to get a quick answer to a 4 week old problem i am having.  I have installed Bodhi 2.3.0 32 bit on an old HP Pavillion 533w with 2Ghz processor and 1G RAM.  I am having problems with their distro not catching my wifi adapter card that i have installed.  They have mentioned i need a driver which i downloaded and a linux header to compile i think together and i don't have a clue how to do this and was going to see if anyone could give instructions on how to accomplish it.

a few items they asked me to run here are:

Lspci – nn | grep -i net

01:09.0 Network controller [0280]: Ralink corp. Device [1814:5392]

01:0d.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL -8139/8139C/8139C+ 
[10ec:8139] (rev 10)


lsmod | grep rt 

parport_pc  32114 1
parport        40930 3 ppdev,parport_pc,lp


iwconfig

lo   no wireless extensions.
Etho no wireless extensions. 						 						

____________________________________

they asked me to download the driver for the wifi card:

This is the page where the linux driver can be found. [LINK]("http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501")  Click on RT539xPCIe, fill in the data and save the file where you can  find it back. Then copy it over to your bodhi partitition.

_____________________________________________________________

and they want me to download a kernel file also:

You also need the kernel headers to create the driver module. You can find that package [HERE]("http://packages.ubuntu.com/precise-updates/i386/linux-headers-3.2.0-35-generic/download")

_______________________________________________________________________________________

Anyone have an answer to what they are seeing here?  Please give me instructions as i am a really bad novice at this and i was trying to get this up soon to give away as a donation to the needy setup by refurbishing old hardware to give away to hands that normally don't get pcs.  Thanks for your help and have a good day!

---

### Post by oldos2er on 2013-06-09
Moved to Other OS/Distro Support.

---

### Post by primitive1 on 2013-06-10
any one have a clue how to build a driver for this?  Can you use a windows driver if you only have linux loaded on your pc?  thanks,

---

