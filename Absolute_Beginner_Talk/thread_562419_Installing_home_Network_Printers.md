---
title: "Installing home Network Printers"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by mlrustich on 2007-09-28
Hi

I am new to Ubuntu and I would like to leave Windows behind, but the last thing that keeps me going back to XP is that I can not for the life of me set up my network printers. We have 4 computers networked in our family home and we all share the Konicia Minolta 2400w printer, we also have a Brother MFC-425CN for scanning-faxing and a Epson Stylus Photo R210 for printing on CD & DVD disk we create, XP networked allows us to access all of them. 

I love Ubuntu for speed and control, but as you can see, what good is a printer if you can not print.

Also I am not as proficient in terminal as some, but I have a rough idea off how it works, and this a problem when you search for how to on the net, you get all this terminal stuff that can confuse.

Can you please help with some easy to understand advise.

Regards
Mick:  :confused:


Ubuntu
Windows XP

2 x Laptops
2 x Desktops

Konicia Minolta 2400w printer,
Brother MFC-425CN for scanning-faxing 
Epson Stylus Photo R210

---

### Post by bruce89 on 2007-09-28
Not that this will help, but in Gutsy, printers are set-up automatically and detected on the network automatically.

---

### Post by chromel123 on 2008-02-15
I have never posted here before, but I'll start by saying that I wanted to give Ubuntu a try...and it is cool.

I like to solve computer problems, though I am no expert on any of it.

I have a Trendnet USB print server, hooked to an HP7550.  In reading the linuxprinting.org web site, I found some useful stuff.  The same general rules apply to both a discrete print server device as well as the built-in ethernet a la the HP 6180, I think.

First, the USB print server "grabs" and holds an IP address as long as it is on.  If I power down the network, the device will grab a new IP address.  So, I try not to power down frequently as I have to go an reset all the IP printing ports to the new IP address (Windows boxes).

My USB print server, for this example, has an IP address of 192.168.1.104   Again, as long as it stays on, that will not change.

I found a nifty terminal command called nmap.  You type like this:

nmap 192.168.1.104

My output was:
PORT          STATE          SERVICE
80/tcp         open            http
81/tcp         open            hosts2-ns
515/tcp       open            printer
9100/tcp     open           jetdirect

The last entry is important!!  Basically what nmap is saying is that the print server has print information conduits in it and as long as  I pour in good printer data, the server will send it to the printer and bingo!

In the administration > printers, I did the "add printer" thing.  I chose the last entry, the most basic "URI" and typed in the following:

socket://192.168.1.104:9100

That nomenclature is socket://{IP of the print server}:{jetdirect port}

After that, it was the standard select a printer, select a driver, select a location, etc.

I do not believe this requires SAMBA, though I loaded SAMBA previously to hook up to a deskjet 930 hooked to a Windows box.

The other port, the 515 port, I think can use another method of printing called LPD.  I'm going to try that sooner or later, but for now I am totally happy.

BTW, the Add Printer did not recognize my print server printer, only the one connected to the Winbox.

---

