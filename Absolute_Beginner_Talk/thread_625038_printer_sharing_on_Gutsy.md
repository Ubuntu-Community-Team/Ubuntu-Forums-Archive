---
title: "printer sharing on Gutsy"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by nemesis8601 on 2007-11-27
I'm currently running Gutsy dual boot with Windows XP, and I'm sharing a printer over a router through XP with another desktop running Windows only. Is there a way for me to print from Gutsy even though it's connected through a router to a Windows computer?

---

### Post by Sinkingships7 on 2007-11-27
i have this same problem.

only i decided to ditch windows a few days back (see sig), and i'm starting to think i want it back.

---

### Post by nemesis8601 on 2007-11-27
Yea, this sucks. I'm thinking every time I need to print I should just boot to Windows or get my own printer. 

On another note, is it possible to share folders with a Windows user over the same router?

---

### Post by Sinkingships7 on 2007-11-28
i'm doing it. so i guess so. just go to places -> network and there should be an icon that says "windows network". at least, that's how mine is. i had my windows configured with the  other computer in the house before i installed ubuntu. i don't know if that had anything to do with it, but i never configured the network within ubuntu... it was just kinda there when after installed it.

---

### Post by master_kernel on 2007-11-28
I'm not sure I understand. I have another computer running Windows and I connect to it and can print through Gutsy to the printer attached to the Windows computer.

Is this your map?
#1. Gutsy > Router > Windows XP(printer)
or is it this
#2. Gutsy(printer) > Router > Windows XP

---

### Post by nemesis8601 on 2007-11-28
my map is

 Gutsy > Router > Windows XP computer with printer on USB

---

### Post by stchman on 2007-11-28
Here is an Ubuntu wiki on having a printer on Gutsy/Feisty/Edgy sharing with XP and 2000 machines.

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

Let me know how this works.

---

### Post by nemesis8601 on 2007-11-28
I looked at the wiki, and when I went to add a printer, I got the following picture. The printer I'm using is an HP PSC 1400, which doesn't show up, but an Epson and Canon do, though. strange...

---

### Post by stchman on 2007-11-28
> **nemesis8601 said:**
> I looked at the wiki, and when I went to add a printer, I got the following picture. The printer I'm using is an HP PSC 1400, which doesn't show up, but an Epson and Canon do, though. strange...

Use the hpijs driver.

[http://openprinting.org/show_printer.cgi?recnum=HP-PSC_1400](http://openprinting.org/show_printer.cgi?recnum=HP-PSC_1400)

---

### Post by nemesis8601 on 2007-11-28
When adding a printer, I have to select the connection (the uploaded picture). I don't see an HP printer on there, so I'm assuming I should click 'Other' and add a device URI, but I don't know what that is. Would I have to find that on the Windows machine? I'm not good with networks and sharing.

---

### Post by lintoon on 2007-11-28
Check this post regarding setting up your ubuntu box to print to a printer connected to an xp box.

[http://ubuntuforums.org/showthread.php?t=519779](http://ubuntuforums.org/showthread.php?t=519779)

Go to System-Admin-Printing and add a network printer and enter your details.

Quote from post:

"For hostname I entered the XP box's IP address 192.168.1.34.
For Printer I entered what I'd labelled the printer in Sharing printer on the XP box, HPOffice.
For username I entered my XP PC name and my XP login name, OFFICEPC\Monty.
For password I entered nothing as I don't use a password to login on my XP box."

The only thing you should have to change is the IP address (or enter the name of your xp machine) and also your username and password of the xp box.

---

### Post by Gildp67 on 2007-11-28
well Ive been spending the last days trying to get my machine (Ubuntu) to share a printer with no luck so I switched the printer over to the windows machine and poof everything works great. I can print from any of the computers in the network Ubuntu or Windows. So for me thats good enough.

---

### Post by master_kernel on 2007-11-28
Choose Windows Printer with SAMBA and go from there. You should know the hostname of the Windows computer. Post a thumbnail if you get stuck.

---

### Post by nemesis8601 on 2007-11-29
Under "Windows Printer via SAMBA", the window prompts me for "smb:/"  and asks for a port. Is this a port I open on my computer or on the XP machine, and what port number should I use?

Also, is it necessary to check "authentication required", and if so, what username and pwd should I use? I saw the thread on sharing printers with an XP printer, but I'm not sure why I'd need to put in username and password. Can you explain that?

Thanks!

---

### Post by lintoon on 2007-11-29
If it's asking for port I imagine it's the path to the xp printer ( smb://your-XP-IP_Address/XP_Printername) eg smb://192.168.1.5/HPlaserjet  

Check these step by step instructions.

[http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-computers.html](http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-computers.html)

One thing I must point out is that if your XP pc has it's IP address set by DHCP you may be able to print today but not tomorrow because tomorrow it may have a different IP address.  If this is the case you may want to set it manually or configure your router to assign a particular IP address to the MAC address of your XP pc.  

The username and password you have to use is the username and password you use on your XP box.

---

### Post by nemesis8601 on 2007-11-29
I've input the IP for the xp computer, printer name, printer driver, user name and password, but I still couldn't print a test page. The printer driver is installed on the windows computer, but is there anything else I have to configure on it?

---

### Post by lintoon on 2007-11-30
Try this on your XP PC:

1. Go to Control panel -> Printers & faxes
2. Right-click on your Printer -> Properties -> Ports tab
3. Uncheck "Enable bidirectional support"
4. Click Apply then OK.

---

### Post by lintoon on 2007-11-30
Also, taking a step backwards I think you should also confirm that the Ubuntu box is communicating with your XP PC.

On your Ubuntu PC open Terminal and type in:

ping -c4 IP_ADDRESS_OF_YOUR_XP_PC

eg ping -c4 192.168.16.1

The output will be similar to this:
PING 192.168.16.1 (192.168.16.1) 56(84) bytes of data.
64 bytes from 192.168.16.1: icmp_seq=1 ttl=64 time=0.149 ms
64 bytes from 192.168.16.1: icmp_seq=2 ttl=64 time=0.155 ms
64 bytes from 192.168.16.1: icmp_seq=3 ttl=64 time=0.156 ms
64 bytes from 192.168.16.1: icmp_seq=4 ttl=64 time=0.142 ms

If you get a similar output great they are talking to one another and you should carry on troubleshooting printer setup.  If not you have a network problem.

I just thought we should go through the above because we could be barking up the wrong tree with our troubleshooting.

---

### Post by nemesis8601 on 2007-11-30
Hmmm.

Windows printer settings was fine, and my computer could talk with Windows computer. When I tried printing a test page from the printer configuration screen, the printer made noises like it was warming up and getting ready to print, but then just sat there. 

When I opened up a random document and tried to print that, the printer queue showed it as processing for about 10 seconds, then for some reason deleted it. Is the spooler clogged, or does anyone know whats wrong? I'm starting to think it's the windows end that isn't working.

I figured that I set up the wrong printer driver on SAMBA, so I dled HPLIP but when I tried to set it up it couldn't detect the printer wirelessly, even though the XP computer had its firewall disabled and I could ping. I'm pretty sure I used the wrong driver, but now I can't install the right one. Does anyone have experience with this?

---

