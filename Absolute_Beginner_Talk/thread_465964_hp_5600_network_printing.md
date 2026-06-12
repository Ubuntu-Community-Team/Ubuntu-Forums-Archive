---
title: "hp 5600 network printing"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2007-06-06
On our network there is a printer installed on a windows machine its a hp 5600 printer.have installed printer driver but when I try to print over the network nothing happens.Can someone help me give me advice as to what to do to get it to work.thanks In advance to the person who helps

---

### Post by Seisen on 2007-06-06
Is the printer set up to be shared?

---

### Post by dstew on 2007-06-06
It sounds like you want to print to a "shared" printer, that is, the printer is directly connected to a Windows machine. If so, you need to do two things. First, you need to "share" the printer in XP, if this hasn't been done already. Then, you need to create the printer in your Linux system as a Samba device. Samba is the Linux software that lets you connect to Windows shared folders and printer. Samba should already be installed on your machine.

In whatever dialog you use to create the printer in Linux, set up the printer as a Windows printer via Samba. You need to use a device name like smb://servername/printername in your printer setup dialog. For example, my shared printer downstairs on my wife's machine is named smb://MARYS/Printer2. The Windows machine name will be the servername, and the Windows printer name will be the printername.

The other issue is the printer driver. Usually you can pick this from a list at the time you create the printer in Linux. I used the CUPS administration tool web page ([http://localhost:631/admin](http://localhost:631/admin)). One issue there, make sure you select "HP" for the printer manufacturer, and not "Hewlitt-Packard". The latter list is missing most of the drivers.

---

### Post by jonathan21 on 2007-06-07
the following error message is attached

---

### Post by dstew on 2007-06-07
You have put the device name "smb://logical/BLESS" into the Location space, but that is not where it goes. In location, you should put the location of the printer, like "Downstairs" or "Room 101" or wherever.

You should go to the Connections tab, click the Network printer button, and choose Windows printer (SMB) from the list. Then, put the host name into the Host space, and the printer name into the Printer space. From the device name above, it looks like the host is "logical" and the printer name is "BLESS", correct? You can also put in a username and password if the host require them.

---

### Post by jonathan21 on 2007-06-27
I did not set my pc on the domain now printing thanks

---

