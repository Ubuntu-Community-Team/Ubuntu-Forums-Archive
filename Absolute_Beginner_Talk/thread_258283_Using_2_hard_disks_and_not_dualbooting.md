---
title: "Using 2 hard disks and not dualbooting"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-09-15
After 4 weeks of using Dapper I decided I had enough problems using Gnome-PPP. Each connection log showed problems with PAP and CHAP. With help from Linmodems.org, I was able to use WvDial instead of Gnome-PPP.

But this wasn't the first set of problems with dial-up and Ubuntu. I removed the ActionTec PM560LKi controller based internal modem from the pci bus. Next I got a Creative ModemBlaster Flash 56 EXTERNAL modem. Once the serial cable, phone line and power supply were attached I turned the modem on. Various leds lit up. So I pushed the computer on-off button and fired up Ubuntu, thinking the OS would find the new modem. It didn't. Or it couldn't. So, I turned off the external modem. Shut down the OS. Unplugged the line cord to the computer, reinstalled the PCI-bus modem, closed the box, powered up and LO AND BEHOLD, now Dapper couldn't find the old modem. Yikes! As I don't have a uSoft partition or software I am without a way to get help on the net.

Finally I posted a question at this Absolute Beginner forum, asking for the commands to make Dapper "see" the modem. The response didn't find a solution. And eventually I decided on a clean re-install. Using the Canonical supplied CD, I re-installed Dapper. No problems were reported with the re-install.

Then in a terminal I sudo-ed: wvdialconf /etc/wvdial.conf. The program ran and reported there was no modem installed. Yikes! It had found it before. So, I shut down and powered up again. And sudo-ed again and was told there was no modem installed. So, I removed the internal modem, set up the external modem and powered up, again. Then sudo-ed again and again I was told there was no modem (serial device). Now I had no way to the 'net. 

So I took the 40 gig drive out of this Dell, put in a 10 gig and installed Dapper again (well, 1st time on this hard disk). Sudo-ed wvdialconf /etc/wvdial.conf. The software found a modem /etc/ttyS4.

Thank you for reading this for to where your help is needed.

Now please give me all the instructions and commands for adding a 2nd hard disk and then moving all that is on /home on that 2nd disk onto the 10 gig (primary master). I don't need help with making the 40 gig a primary slave. Then I need to reverse the process, reinstalling and in effect wiping the 40gig, making it primary master, and the 10 gig primary slave and finally moving all the /home.

Currently the 10 gig is the primary master and has a working Dapper.

The 40 gig has the "old" /home that must be moved to the 10 gig and then once the 40 gig is "reformatted" and Dapper up and running, I will move /home back onto it from the 10 gig.

The 40 gig has an hda3 partition that holds the Breezy /home (and all other files as well).

Can Dapper "see" both hard drives and allow me to move /home from HDD to HDD?

Thanks for your patience wading through all this.

---

