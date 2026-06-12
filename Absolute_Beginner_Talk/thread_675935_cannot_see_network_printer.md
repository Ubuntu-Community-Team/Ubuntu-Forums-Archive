---
title: "cannot see network printer"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2008-01-23
I am unable to see some shared printers on out network these pc's use windows and i am using gutsy. tried adding printers via samba

---

### Post by insineratehymn on 2008-01-23
I had this problem and all I had to do was restart cups on the server.
In terminal:

/etc/init.d/cupsys restart

Let me know if that works.

---

### Post by mikeyphi on 2008-01-23
> **jonathan21 said:**
> I am unable to see some shared printers on out network these pc's use windows and i am using gutsy. tried adding printers via samba

Are these 'Network Printers' or printers connected to networked computers?

---

### Post by silverj on 2008-01-23
Hello,

Assuming they are printers on networked computers, have you shared your printer(s) on your windows machines?
Right click on the printer you want to share and select 'Sharing' or equivalent. You give it a name then you should see it.
I've just been through this and it worked for me...

---

### Post by jonathan21 on 2008-01-24
they are shared. this problem has only started since gutsy.have been able to access them before so i don't know whats changed.and they are printeres shared on windows machines

---

### Post by mikeyphi on 2008-01-24
> **jonathan21 said:**
> they are shared. this problem has only started since gutsy.have been able to access them before so i don't know whats changed.and they are printers shared on windows machines

If they haven't worked since you installed gutsy - it might be that all that's needed is to open System/Administration/Printing and check the options

Double check that you've enabled sharing on the system(s) that have the physical connection to the printers

---

### Post by matjazcr on 2008-01-31
I have a similar problem. I am connected to windows domain and can access the shared files and folders well. But I cannot connect to the printer (Canon Pixma MP530) connected through UBS to one of the workstations. When I go through System-Config Printer/Add Printer and choose "Windows printer via SAMBA", I can see the workstation but not the printer attached to it.
I have triplechecked that the printer is connected and properly shared in the XP there. Other XP workstations can print to it. Some helf would be very much appreciated.

---

### Post by oedha on 2008-01-31
if the printer is shared....
you just hva to go to system > administration > printing
click new printer....choose windows priter via SAMBA.....

~E~

---

### Post by matjazcr on 2008-02-01
That exactly the problem:I "choose windows printer via SAMBA", see the domain and the workstation, but NO printer connected to it, although it is turned on and seen by other (Win XP) workstations.

---

### Post by Jerry N on 2008-02-01
If I understand correctly, you can't see the printer when browsing the network.  I have had the same situation with Ubuntu and LinuxMint and have to explicitly tell the printer install system where to find the network printer (the server name) and the share name of the printer.  I then have to tell the printer install system what model of printer to install a driver for.  I just assumed it was supposed to work that way.  It's not like WinXP which will automatically find the printer and install the correct driver, assuming of course that the printer is old enough to be in the WinXP SP2 database.  

I don't recall for sure  but I think it was the same for Freespire, Linspire, and LinuxMint Fluxbox.  

Jerry

---

### Post by matjazcr on 2008-02-01
I have tried that as well, but with no success.

---

### Post by StarscreamD on 2008-02-15
I have the same printer, a Canon MP530, and I am not able to view the networked printer using Konqueror in Gutsy. The printer is connected via usb to a windows xp workstation and I am attempting to install the printer using samba. Printer Sharing is enabled on the workstation connected to the printer. I have also tried to install by entering in the information manually but I still cannot get it to work. I recently upgraded to Gutsy an reinstalled my printer, so I think the problem stems from the upgrade. This printer worked great in Feisty.

Has anyone got this specific printer to work?

---

### Post by oedha on 2008-02-15
have you spend some time to wait.......cos it will take time to load
or
have you try to type down the address

---

### Post by StarscreamD on 2008-02-15
oedha: I have waited as long as my patience will allow. Over 5 minutes and still nothing. On a side note, using Smb4k I am able to see the networked printer! How can I use samba to get this dang thing installed now? It's still not viewable under Konqueror

---

