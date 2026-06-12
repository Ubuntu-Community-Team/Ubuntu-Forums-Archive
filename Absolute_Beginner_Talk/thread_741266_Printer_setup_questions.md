---
title: "Printer setup questions"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by MrPaez on 2008-03-31
I have a HP Photosmart C6280 network capable printer. The printer has an assigned IP address. I would like to add the printer to my Ubuntu box and have the same desktop act as a printer server  for my non-linux laptops and desktops.

Can someone guide me through the process or any suggestions on where to start? By the way it appears that I have the HPLIP software already installed on my desktop.

Well I found an answer using the powerful Google:
[https://answers.launchpad.net/ubuntu/+question/15868](https://answers.launchpad.net/ubuntu/+question/15868) 

I went through the CUPS interface through Firefox. Now I need to see if I can find an exact PPD match for my printer.

---

### Post by Joe325 on 2008-03-31
Is this printer plugged directly into a router- is this how the ip address has been determined? 
I have a 6180 network / wireless printer and have it configured wirelessly to my network. This printer doesnt rely on any machine/server being left on to print, also the laptops print to it from anywhere.

---

### Post by stchman on 2008-03-31
> **MrPaez said:**
> I have a HP Photosmart C6280 network capable printer. The printer has an assigned IP address. I would like to add the printer to my Ubuntu box and have the same desktop act as a printer server  for my non-linux laptops and desktops.

Can someone guide me through the process or any suggestions on where to start? By the way it appears that I have the HPLIP software already installed on my desktop.

Well I found an answer using the powerful Google:
[https://answers.launchpad.net/ubuntu/+question/15868](https://answers.launchpad.net/ubuntu/+question/15868) 

I went through the CUPS interface through Firefox. Now I need to see if I can find an exact PPD match for my printer.

You need to give the printer an IP address.  If you ar hooking it up to a router then assign the printer an IP outside your router's DHCP.

Example if your router's IP is 192.168.1.1 and it's DHCP is say 192.168.1.100 to 192.168.1.150 then assign the printer an IP of 192.168.1.160.

Next fire up the Print Manager in Ubuntu and select Add.  The printer with IP should come up in the window.  Select it and selct an appropriate printer driver.

Now that printer is no listed in the openprinting database so you may have problems getting it to work with Ubuntu.

---

### Post by MrPaez on 2008-04-02
Hey guys to answer your questions.

The printer was connected directly to the router and I entered in a static IP address on the printer.

I was able to use CUPS to add the printer to my computer, thanks for all of your help with this.

---

