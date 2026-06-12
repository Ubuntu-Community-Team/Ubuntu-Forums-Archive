---
title: "Really Need help with printers !!"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Accurax on 2007-04-23
Guys im stupmed... ive got an hp officejet 7400 seires on a network, and I desperatly need to be able to print to it.

Ive tried installing hplip (whatever that is) but i just get dependancy errors and it doesnt actually seem to do anything after its installed.... and i dont know how to uninstall it and try again.

Yes, i am a linux noob .... but jesus H i need help with this .... I just dont understand at all..

Arrrggghh

Im about to throw my pc out of the window, 4 hours to setup a damn printer is bloody stupid and im starting to regret changing my laptop to linux at all.... please please someone help me here.

---

### Post by Accurax on 2007-04-23
shamless bump

---

### Post by irw on 2007-04-23
Obvious points first: 
1. the printer is connected and switched on?  (this had me stuck for ages!!)
2. Does the printer work with other computers?
3. Does the computer connect to the network OK - can ou communicate with other computers on the network?
4. Can the computer detect the printer? what model does it think it is? What errors are you getting?

According to [linuxprinting.org]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_7400") your printer should work, so don't give up yet!

---

### Post by lukew on 2007-04-23
> **Accurax said:**
> Guys im stupmed... ive got an hp officejet 7400 seires on a network, and I desperatly need to be able to print to it.

Ive tried installing hplip (whatever that is) but i just get dependancy errors and it doesnt actually seem to do anything after its installed.... and i dont know how to uninstall it and try again.

Yes, i am a linux noob .... but jesus H i need help with this .... I just dont understand at all..

Arrrggghh

Im about to throw my pc out of the window, 4 hours to setup a damn printer is bloody stupid and im starting to regret changing my laptop to linux at all.... please please someone help me here.

Have you tried turboprint?

Got my old epson stylus colour 600 working! :)

---

### Post by nickpaton on 2007-04-23
Have a look at this:

[http://hplip.sourceforge.net/troubleshooting/network.html]("http://hplip.sourceforge.net/troubleshooting/network.html")

Initially disable the firewall on your ubuntu pc.  To do this install GUI Firestarter via Synaptic and click the disable button.

Once you have got the printer working over the network you should enable the firewall.

This requires a couple of simple steps:

1. Configure your network or modem router to assign the same IP address to each PC / printer on your network each time they are switched on.  

2. Set up Firestarter.

The link below gives some information on how to do this:

[http://ubuntuforums.org/showthread.php?t=202605&page=30#298]("http://ubuntuforums.org/showthread.php?t=202605&page=30#298")

HTH

---

