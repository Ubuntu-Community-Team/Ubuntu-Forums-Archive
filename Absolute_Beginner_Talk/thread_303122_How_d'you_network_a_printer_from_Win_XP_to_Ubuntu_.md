---
title: "How d'you network a printer from Win XP to Ubuntu 6.06?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by newagelink on 2006-11-19
So here I am with Ubuntu 6.06. My mom's laptop is Windows XP, and we have a Belkin router.

I've got an ethernet cable connecting my laptop to the Belkin router because I couldn't figure out how to set up the wireless connection. I thought I had correctly entered the Domain name, SSID/ESSID (same thing?), and WEP, but whatever, it still wouldn't work.

So I gave up on that; I don't have the time (or intelligence, it seems) to figure it out.

So now I'm wondering, is it possible for me to network our printer? I did it once using Windows XP, but now that I'm in Ubuntu I don't even know if it's possible to connect to a network with other Windows computers. Her McAfee firewall might block me, as well. (I tried it in Windows XP and whenever I tried connecting to her laptop (Toshiba) it kept asking me for a Guest password. Why?)

Is it? With the printer connected to my mom's Windows XP laptop, is it possible for me to "network" to it and print from it in Ubuntu?

---

### Post by SomeGayDude on 2006-11-19
Yes you can network the XP printer.

On the XP box goto the printers folder.
Right click on the printer you want to network.
Click on Sharing tab.
Click on the Share As thingy.
In the box type "Printer" or something that you want to call it.
Click on OK.

Now, on the ubuntu box
Goto System/Administration/Printing
Double Click on New Printer
Click on Network Printer thingy.
Now the URI will be somthing like //server/printer   (I think)

The server part is the host, or your computer name.

Winders Xp has a user account for Guest.  It is deactivated by default.  You might need to change the printer user list, but I have no clue on that.  McAfee should come up with a popup asking to allow or deney access.

---

### Post by newagelink on 2006-11-19
Thanks a lot! Gonna try it now ...

Um, in the Add a Printer window I have a choice of Network Printer
[LIST]
[*]CUPS Printer (IPP)
[*]Windows Printer (SMB)
[*]UNIX Printer (LPD)
[*]HP JetDirect
[/LIST]
I'm thinking Windows Printer, but it then asks for authentication for my computer and for hers, and I'm still confused about authentication to connect to her computer.

---

### Post by newagelink on 2006-11-19
Her Gateway just died -- I was mistaken about the model; my father's is a Toshiba.

Her computer just died -- again. It shut off, and now when we press (and/or hold down) the power button, nothing happens.

Something about a short of the power supply; she sent it off before (it was under warranty then), they replaced the power supply with a 90 day warranty. Three months later, same thing happens, this time not under warranty.

Seems Gateway is a crappy computer company. My Gateway has problems (and it's only a year old), hers died (had shorts in both power supply and monitor), and my brother's Gateway randomly shuts down he says.

I know this is off topic, but it's frustrating. (Firefox crashed when trying to open a PDF file in a tab -- the latest version -- she restarts computer, and it shuts off and doesn't start back up. We were about to [print things]("http://mtsu.edu/~phys2110/HW_Format/hw_format.html") for homework.)

---

### Post by SomeGayDude on 2006-11-20
Opps, It's been a while since I setup my printer.  You would choose Windows Printer (SMB).  I've heard that the older gateway machines was trash.  I have never owned one myself.  Do you plan on getting it fixed?  I remember a few time I lost my homework from computer crashes.  The worst was the 10 page essay I had finished and I lost the hard drive.  I kinda failed that class.  Best of luck.

---

