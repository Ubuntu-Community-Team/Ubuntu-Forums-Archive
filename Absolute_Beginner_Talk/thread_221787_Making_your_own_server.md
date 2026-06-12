---
title: "Making your own server?"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-07-24
Some in my house *need* windows, so we have a couple windows machines.  But you have to reinstall two or three times a year (such is the nature of windows), and this proccess is tedious, because I have to reinstall the printer, and set up the network again.  I was wondering, could I have an old laptop run linux and install the printer and set up the network on it, and when I reinstall on the windows machines I can just connect to the linux laptop?  I'm very new at linux, and I've never actually networked my linux machines to the windows machines (I merely connect to the internet through DHCP) so I'm not sure how if I can do this.  And I'm not sure if you can install our printer one linux, it is a very complex printer/scanner/fax machine, can you use wine to install it?  Anyway, I was also wondering, is what I'm describing a server?

Alternatively, if I can convince all to switch to linux, what is the easiest way to network them, and can I install said printer to Ubuntu?

---

### Post by mssever on 2006-07-24
Whether or not your printer will work under Linux depends on the make and model of the printer.

Assuming that your printer works, you have two options:
[LIST=1]
[*]Install Samba, which makes your Linux computer be able to share files and printers just like if it were running Windows. Configuring Samba isn't as easy as it could be, though. Also, there's a bug in Windows XP that sometimes makes printing under these conditions terribly slow (like 30 min per page sometimes). If you are willing to mess with the Windows registry, the workaround is to delete a bunch of keys (HKEY_CURRENT_USER\Printers, if my memory serves me correctly).
[*]Install it normally on your Linux computer, and tell your Windows boxes to add a network printer at the following address: [http://192.168.1.1:631/printers/printer_name](http://192.168.1.1:631/printers/printer_name). Replace 192.168.1.1 with your server's IP address (servers should always use a static IP address) and use the name assigned to the printer when you installed it as the printer-name in te URL. I haven't done this option from Windows, but I've heard that it works better than the other one for Windows XP. And, it works great from Linux to Linux.
[/LIST]

---

