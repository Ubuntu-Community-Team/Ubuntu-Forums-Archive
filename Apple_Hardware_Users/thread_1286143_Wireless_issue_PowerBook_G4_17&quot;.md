---
title: "Wireless issue PowerBook G4 17&quot;"
date: 2009-10-08
forum: Apple Hardware Users
---

### Post by buntybuntu on 2009-10-08
Hi All,
 
I have successfully installed Ubuntu 9.04 (Jaunty Jackalope) on my PowerBook G4 17". Everything works.. almost.
 
The issue I am having is with my wireless. Ubuntu is using fwcutter and wireless works great... until I restart my computer. Once I restart, ubuntu forgets the network it connected to last time and also the password used to connect to the network. I can connect to unsecured networks with absolutely no problem.
 
I am using WAP Personal and my router has been told not to broadcast the SSID. 
 
Once I restart, the hidden SSID is not discovered, and after multiple times deleting and creating the connection, reentring the password the system connect just fine and stays connected for as long as I do not restart.
 
Where is this information saved? Can I go into some config file and hard code the SSID and password so that it is "Remembered"?
 
Thanks in advance
buntyBuntu

---

### Post by noibs on 2010-01-21
I have exactly the same problem with a 15" titanium Powerbook.

A few days ago I installed Ubuntu 9.10 on an 867mhz Powerbook.  Pretty much everything works--but it will not remember a hidden wireless network between restarts.  Actually, that's not correct.  It remembers the network name, but it will not auto-connect to that network after a reboot.  In addition, if "Connect to hidden network" is selected in the network panel, the hidden network name is available from the last session; however, selecting that network still doesn't allow a connection.  You have to manually type the name of the hidden network after each restart.  As long you don't restart, you can close and open that connection, or select another wireless network and then return to the original hidden one all without any problems.

I even tried entering the hidden network settings with the MAC ID number of my cable modem.  No dice.

Oddly, I had previously installed the lastest version of Debian about 3 weeks ago onto this same computer.  It had no trouble auto-connecting to the same hidden network.  Go figure.

Any help or advice would be appreciated.

---

### Post by linuxopjemac on 2010-01-22
cannot you save the settings is gnome-networkmanager? I don't use a hidden SSID at home, but I did save my WPA password and SSID in the manager and it always reconnects after a reboot.

---

### Post by noibs on 2010-01-22
Yes, you can save the settings.  And, as you said, for not-hidden networks, everything works fine and the computer will auto-find the designated network after booting.

However, when the network is hidden, it simply will not auto-connect after booting.

It has to be a bug, because my same network will auto-connect after booting if it's not hidden.

It's not the end of the world.  If my Powerbook was something I used everyday, I would likely change the security framework of my network and not hide it any more.

---

