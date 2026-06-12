---
title: "Printer won't print"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-05-06
Edgy sees my printer & when I try to print a test page my printer shows that it is "receiving data"
but it won't print anything. It's like it doesn't know what to do with the data being sent.
I've downloaded & installed the printer drivers from the Brother printer website.
Mt printer is a Brother MC-420CN & it doesn't show up in the driver list but it defaults to the MFC-6550MC on installation & the download file says its for my printer on the site. 
Any ideas?
My printer works in Win98 which I'm dual booting with Edgy so I know there's nothing wrong with my printer or usb connection.   
system/administration/printing/MC-420CN (Brother/default printer)/properties
In the printers Genral tab under description it says MC-420CN but under location its blank. 
If this is not the right group to ask this question could someone please point me in the right direction.

---

### Post by tatimmer on 2007-05-07
I had a similar problem with my HP.  The following may be helpful to you.

printer
"lpc status" provides some data on your printer
ubuntu breezy has a bug, for HP deskjet 712:
edit /etc/pnm2ppa.conf and add "version 712" 
no need to reboot, this file is read with each print operation

---

### Post by intMain on 2007-05-28
Use this guide [https://help.ubuntu.com/community/PrintersBrotherMfc420cn](https://help.ubuntu.com/community/PrintersBrotherMfc420cn)

You might need to install a couple of more packages in addition to configuring your printer through CUPS ( [http://localhost:631](http://localhost:631) )

---

