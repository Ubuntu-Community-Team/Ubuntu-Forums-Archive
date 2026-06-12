---
title: "Making a HP laserjet 1022 work in Ubuntu"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Neil Purling on 2007-04-04
I set up a Laserjet 1022 as part of the installation and I can see a queue of jobs present.
Even the test page isn't printing. Anyone got Ubunto and one pf these printers?
Is there another listed driver that works this printer?

---

### Post by mikeyphi on 2007-04-04
> **Neil Purling said:**
> I set up a Laserjet 1022 as part of the installation and I can see a queue of jobs present.
Even the test page isn't printing. Anyone got Ubunto and one pf these printers?

I'm don't have one  - but suggest you check (if not already done!) under SYSTEM - ADMINISTRATION - PRINTING.....highlight the HP and select EDIT....check all settings are appropriate.
I'm assuming the printer is directly connected and not networked?

---

### Post by benner on 2007-04-04
i have one set up at my school with edubuntu feisty.  it works fine.  it was already there in the setup wizard 'use a detected printer' box.  i doubt i could help you beyond letting you know that mine works.  sorry you're having trouble though.

---

### Post by hashimoto on 2007-04-04
Some experience here:

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1022](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1022)

---

### Post by hashimoto on 2007-04-04
Just found another thread here: [http://ubuntuforums.org/showthread.php?t=400125](http://ubuntuforums.org/showthread.php?t=400125)
which guides you to install hplip here: [http://hplip.sourceforge.net/index.html](http://hplip.sourceforge.net/index.html)
Your printer is supported by hplip driver

---

### Post by Neil Purling on 2007-04-04
I have the file 'hplip-1.7.3.run' on my desktop.
I type "sudo sh hplip-1.7.3.run" in terminal. I am asked for my password & give it but this is what I get

neil@neil-desktop:~$ sudo sh hplip-1.7.3.run
sh: hplip-1.7.3.run: No such file or directory


Should the file be in a different place, or do I need to type something else?

---

### Post by Neil Purling on 2007-04-06
I have copied the file 'hplip-1.7.3.run' to my home folder and I still get 'command not found' in terminal.
Have I missed out something I should have added?
What should I type in terminal to get this to install itself?

---

### Post by Neil Purling on 2007-04-06
Hey benner: If a HP1022 works with edubuntu feisty maybe you should tell me what settings the printer has? 
Are there any material differences between Edubuntu feisty and Ubuntu dapper?

---

### Post by Neil Purling on 2007-04-08
I got the printer to work by changing connections and editing of the printer properties. It's now plugged into one of the network ports and I made sure to take a screenshot of the settings that worked for me.
I don't know if they are of any use to anybody else, but here they are anyway.

---

### Post by davidsiegel on 2007-04-08
I use an HP Lasertjet 1022 with Edgy and Feisty. I have it setup as a networked printer, and I use the HP Jetdirect protocol instead of the CUPS protocol you have selected, and everything works like a charm.

On the other hand, my printer is configured through an Airport Express with zerconf networking, so if you're going to use HP Jetdirect I'm guessing your printer has to be networked somehow instead of connected via USB.

David

---

