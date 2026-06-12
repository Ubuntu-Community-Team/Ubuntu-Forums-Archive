---
title: "I can't connec to shared printer on Windows XP"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by linuxcity on 2006-05-09
I'm able to browse the Windows share, but I can't print to the share on the Windows XP machine. The windows has the static ip of 192.168.1.3, shared name is "printer"  without password. The printer is HP laserJet 4100n. Alll Windows are able to print to this shared printer fine.

I went to System =>Administration => Printing =>add new printer 

I have tried //hostname and 192.168.1.3 and \\hostname, but after I tried to print the test page, the printer status says "Pending: printer-stopped "

Am I missing something in the configuration?

---

### Post by user1397 on 2006-05-09
I don't have a reply, but I do have a question!
How did you get to browse your windows share from the linux pc?
did you just go to file browser, and then type in location:"smb://<ipaddress>"?
and did you enable filesharing on your windows pc?

---

### Post by linuxcity on 2006-05-09
I went to "Places| Connect to Server" I can browse those already shared, or connect with the ips address to those that doesn't show up, but I know the sharing point.

---

### Post by user1397 on 2006-05-09
okay thanks for helping me out and sorry for not helping you out!

---

### Post by Daremo on 2006-05-09
You need to enable that printer to be shared. Go to Printer & Faxes (in Control Panel) right-click on the printer you want to share and select Properties. There should be a Sharing tab along the top of the Properties dialog box. Click on the Sharing tab. The settings you need should be there.
If you use the HP installer for the 4100 series I believe there is an option to share it durring initial setup of the printer (at least there is on the 4200 series).

---

### Post by linuxcity on 2006-05-10
The printer is shared already. Other Windows computer can print to it fine. Only I can't print to it because I'm using Ubuntu.  There is driver for 4100, just it did not go through.

---

### Post by _aeon on 2006-05-16
I'm having the same problem... *argh* :( 

Also, if I want to access Windows share folder from Ubuntu, I must type smb://192.168.1.3/... (direct link). With Breezy, I could browse without problems from Nautilus. Oh well...

---

### Post by AndyCooll on 2006-05-16
Have you tried adding a printer?

Administration --> Printing --> Printer --> add printer. 

In the wizard that pops up select "network printer", and choose "windows printer (smb)" then continue adding your printer details as requested

:cool:

---

### Post by popeyeray on 2007-02-10
Same thing here, I have a HP 3055 Laserjet connected via network and usb cable. Have attempted several times to connect to it with no success. Why can't this simple task be done in Ubuntu? It's not ready for the desktop I guess.:(

---

