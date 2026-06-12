---
title: "Installation Help"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by ellannjohnson on 2007-06-18
Hi.
I am new to Linux. I download the ISO image for Ubuntu 7.04 amd64. I burned the image and checked the integrity of the file using winMd55um everything checked out fine. I put the cd in the drive it shows the splash screen which says the browser is loading and then I get nothing. Can anyone tell me where I am going wrong? I am new to Linux, but not new to computer use. I am pretty computer savvy so all I need is someone to point me in the right direction . I really wan to try Linux and install when I find the best version for me. Please help.

---

### Post by sickpuppet on 2007-06-18
Hi ellannjohnson - 

It sounds like you inserted the CD while Windows was running. That won't give you Ubuntu, it'll just give you the option to install some good open-source apps (when it works!).

You need to reboot your machine with the Ubuntu CD in the drive. If the machine diesn't boot off the CD, then you may need to change your BIOS settings to re-arrange the order in which the systems scans for bootable media.

Finally, are you sure that the AMD64 version is the right one for you? What type of CPU have you got in your machine?

regards
Ben

---

### Post by ellannjohnson on 2007-06-18
Ben,
That solved one problem. I did change my BIOS settings so it would boot from the cd rom first. After I did that and restarted my machine during the first booting settings that run when machine first starts up I got the message "PXE-E53 No boot file name received from BINL, DHCP or BOOTP" Now even after I change my settings back so it will boot from the hard drive first it will not boot. It gives the same message and I cannot even access Windows. I have tried to boot it form my Windows OS CD and it will not still. It gives the same message. Help!

---

### Post by ellannjohnson on 2007-06-18
Hey Ben.
I have fixed my Windows problems, but now I am back to getting Ubuntu to run. Like I said I changed my BIOS to boot form the cd rom. It did but I got the following message : DHCP MAC address 03 02 15 02 15 PXE-E53 No boot filename received from BINL, DHCP, or BOOTP. Any other suggestions? I have several machines. Not exactly sure of their specs because they are my little projects. I tinker with building and unbuilding and switching parts in and out whenever I come across spare parts. I will look and post the specs.

---

### Post by sickpuppet on 2007-06-21
Hi ellannjohnson - 

Apologies for the delay in getting back to you!

That message ("DHCP MAC address 03 02 15 02 15 PXE-E53 No boot filename received from BINL, DHCP, or BOOTP.") tells you that the machine is trying to boot from the network, not from CD.

Can you list the choices you have in your BIOS for boot devices? Depending on your BIOS, you should have a way to specify first, second and third boot devices.

Also, what is the version of your BIOS? The brand and version will be on the first screen that comes up after your machine boots - something like "Phoenix BIOS 2005 ...."

regards
Ben

---

