---
title: "Wireless Internet on IBM T42 Notebook"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by Fermanagh on 2005-09-09
I am unable to get internet to work with Live CD version 5.04 and a copy of version 5.1 (Breezy Colony 4) built on 20050317ubuntu15.

When I activate Firefox it dispalys file:///usr/share/ubuntu-artwork/home/index.html and if I type in a real URL adddress, it always retuns "not found"

My network icon tells me that I am connected to "lo" and I can watch it send/receive packets. 

The Live CD versions seem to load up OK and the applications seem to work OK, but I am unable to get onto the network with my wireless router. My IBM T42 is rather new and it runs WinXP Professional and has 1MB of RAM. 

Are there any special boot commands or parameter settings required after the distribution is up and running on my machine to get wireless internet working?

I am new to ubuntu and would like to get the Live CD version working before I do any installs.

Thanks

---

### Post by Kyral on 2005-09-09
First off I doubt you have 1 **MB** of RAM, Windows wouldn't run :P 

Second off, lo is just the loopback device, it cannot connect to the internet. You may wish to give us more info, like the output from lspci

---

### Post by Fermanagh on 2005-09-09
Yes, 
You are correct on the memory.
I have 1GB of RAM.

What is lspci? 
Is it someting that's dispalyed somewhere?

Thanks

---

### Post by Kyral on 2005-09-09
Whoops, sorry. Went Commandline Commando for a second.

Yes, its a terminal command.

---

### Post by Fermanagh on 2005-09-09
I think maybe lspci might be a command that I can run in terminal mode?

Let me know....

Thanks

---

### Post by Fermanagh on 2005-09-09
lspci returns 17 lines
The first line is: Controller (rev 01)
The last line is: Network Controller: Intel Corp PRO/Wireless 2200BG ( rev 5 )

Is there any special line that you need more information On?

---

### Post by Kyral on 2005-09-09
Just cut and paste the entire thing into here

---

### Post by Fermanagh on 2005-09-09
Host Bridge: Intel Corp 82855PM Processor to I/O controller
PCI bridge Intel Corp 82855PM Processor to AGP Controller
USB Controller ...
USB Controller...
USB Controller...
USB Controller...
PCI bridge
ISA bridge...
IDE interface...
SMBus...
Multimedia audio controller...
Modem...
VGA Compatible Controller...
CardBus bridge...
Eithernet controller Intel Corp 82540EP Gigabit Eithernet Controller (Mobile)
Network controller Intel PRO/Wireless 2200BG

---

### Post by Fermanagh on 2005-09-09
Sorry,

I am on my office client machine and my notebook is not connected so its difficult for me to cut and paste.

---

### Post by Kyral on 2005-09-09
Got what I need. The "[Big Database 'o Wireless Cards]("http://www.linux-wlan.org/docs/wlan_adapters.html.gz")" lists it, but no notes on if it works, or even the chipset. I have a stupid question, have you tried going to "System -> Admin -> Networking" and tried to enable it?

---

### Post by Fermanagh on 2005-09-09
OK,

I went to network settings and nothing is setup...

The Wireless and Eithernet connections are not configured.

So, I will logoff and go try and set them up. 

I will need to contact my ISP Roadrunner to get the details...


Thanks for your help..

---

