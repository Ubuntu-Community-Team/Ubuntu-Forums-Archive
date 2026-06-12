---
title: "Network Printer Installation Help"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by drheeder on 2007-10-24
I installed Ubuntu 7.10 yesterday, I'm totally new to Linux, have installed it a couple of times in the past, but this is the first time I'm trying to stick with it. At work we have a couple of networked printers. HP Printers to be exact. From XP I used to connect to the printer with \\server\printername, this doesn't seem to work with Ubuntu. I've tried JetDirect with just the <server> portion and the <server><printer> option. It lets me through to the second page where I can chose the printer myself, but test pages don't print, so I think it's not working. Could anyone please point me to some help on how to get to print to this printer ? I read the UbuntuNetworkPrinting on the wiki, but it didn't really help, and seemed to refer to things that are not there anymore, like the Global settings.

Thank you

---

### Post by realvz on 2007-10-24
Try this:

1. Go into the printers control panel and choose Printer > Add Printer.
2. Select Network Printer and use the listbox to choose HP JetDirect.
3. In the Host box type the IP address of your printer.
4. Click Forward.

---

### Post by drheeder on 2007-10-24
This is what I do:

1. System -> Administration -> Printing
2. Click New Printer
3. Select AppSocket/HP JetDirect
4. Under Hostname I type in the IP address of the server (now we have multiple servers hanging off one point (as is my understanding) in XP this is usually \\<server>\<printer>) But I'm just typing in the <server> bit.
5. Click Forward
6. It then asks me to select my printer, I chose HP, then forward.
7. Then I select Laserjet 4000 on the left and HP Laserjet 4000 Foomatic/hpijs on the right. The actual printer is a Laserjet 4000 N which is not on the list.

After doing all this I get the printer under Local Printers, but when I print a test page nothing happens. Now the only thing I can think of is that the <printer> bit is missing and that's why ?

---

### Post by NIT006.5 on 2007-10-24
I would think if you're connecting *through* a server, you should specify Windows (SMB) instead of HP JetDirect perhaps. I've only used that setting on printers that are connected directly to the network (not through a server). For all others, if it's connected to a Windows server, then I think it should be done as a Windows/Samba printer.

---

### Post by drheeder on 2007-10-24
Great, thank you, SMB was indeed the answer, printing is up and running :)

---

### Post by jasonkwan on 2007-10-25
I'm trying to do the same thing, but how do I find out the IP address of the server?  I know the address with format \\server\printer that I use in windows.

Thanks

---

