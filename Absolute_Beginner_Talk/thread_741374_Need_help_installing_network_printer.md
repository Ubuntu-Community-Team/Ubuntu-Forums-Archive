---
title: "Need help installing network printer"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by nathanscottdaniels on 2008-03-31
Alright well I am sure PO'ed by the fact that my new non-refundable $200 printer is not supported by linux (lazy developers :mad:)  So my only other option is to use my HP Photosmart 7350 which is connected to a print server on my network.  Look at the attached png image for more info.  

I cannot figure out/get it to work under Ubuntu.  It was a breeze with my 4 Windows PCs so I figure this is yet another thing linux does not support.  Am I wrong?  Is there a way?:confused:

---

### Post by cmnorton on 2008-03-31
Ubuntu has a good printer config interface. Have you tried using one of the generic drivers to see if your Ubuntu system can talk to your printer?

What kind of printer is it?

Never say never.

---

### Post by stchman on 2008-03-31
> **nathanscottdaniels said:**
> Alright well I am sure PO'ed by the fact that my new non-refundable $200 printer is not supported by linux (lazy developers :mad:)  So my only other option is to use my HP Photosmart 7350 which is connected to a print server on my network.  Look at the attached png image for more info.  

I cannot figure out/get it to work under Ubuntu.  It was a breeze with my 4 Windows PCs so I figure this is yet another thing linux does not support.  Am I wrong?  Is there a way?:confused:

You will need the IP address of the printer than the print server has assigned to that printer.

Does the add a printer give a list of printers in the window.  It usually does.

That printer works well under Ubuntu.

[http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7350](http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7350)

---

### Post by nathanscottdaniels on 2008-03-31
Its and HP as mentioned above.  I am not sure how to set up a network printer under Ubuntu.  I know that in Windows, there is a wizard you type the server name and printer name and it finds it but IDK what to do here.

---

### Post by nathanscottdaniels on 2008-03-31
The print server never assigned the printer an IP, but the server itself has an IP.  I think you are thinking that the print server is an actaul server, like a computer, but it is just a small little plastic box.

---

### Post by cmnorton on 2008-04-01
> **nathanscottdaniels said:**
> The print server never assigned the printer an IP, but the server itself has an IP.  I think you are thinking that the print server is an actaul server, like a computer, but it is just a small little plastic box.

But usually those print servers have either an application or web interface, so you can go fiddle with them during the setup portion. For NetGear and Hawking, I had to have the print server running on my LAN, so the respective applications shipped with those devices could talk to the print server, and either set it as a static ip server or to get DHCP, for example.

---

### Post by nathanscottdaniels on 2008-04-01
I already set up the server to have a static ip of 2.9.19.93.  I just don't know how to get Ubuntu to see it (the printer) on the network and use it.

---

### Post by cmnorton on 2008-04-02
Try smbclient.

---

### Post by nathanscottdaniels on 2008-04-02
Okay I figured out how to get it to see the printer (on my own) but it doesn't print anything.  Whenever I try, it says "Processing" in the printer status window for about 10 minutes before the job disappears.  I tried all three drivers and they all did the same thing (nothing).  Can anyone help?  It seems as though printing was an afterthought to linux developers...

---

### Post by canthus13 on 2008-04-03
I've discovered that referencing the print server/computer with the printer attached by IP address speeds things up greatly.  I had a similar problem with file shares on windows boxes.  Once I started referencing the IP addresses of the machines in question, rather than the WINS name, connections were nearly instant.

--Me

---

### Post by canthus13 on 2008-04-03
> **nathanscottdaniels said:**
> I already set up the server to have a static ip of 2.9.19.93.  I just don't know how to get Ubuntu to see it (the printer) on the network and use it.

Umm... I can't help but notice that you said you assigned it a public IP.  is your print server connected directly to the internet? 

--Me

---

### Post by nathanscottdaniels on 2008-04-05
When did I say public?  I set it up to NOT use my router's DHCP.

---

### Post by canthus13 on 2008-04-05
2.9.19.93 should be a public IP address.  Valid Private address ranges are 10.0.0.0 – 10.255.255.255, 172.16.0.0 – 172.31.255.255, and 192.168.0.0 – 192.168.255.255.  using the address you have can potentially cause routing problems within your network.  Not using DHCP is fine, but you should still use an address within the range of the subnet being used by your router.  Most home-use routers have a method of reserving certain IP addresses for things like print servers and such.  Check the documentation that came with your router for the exact procedure.

---

