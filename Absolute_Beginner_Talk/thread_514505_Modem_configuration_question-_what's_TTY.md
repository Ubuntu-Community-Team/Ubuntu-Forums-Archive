---
title: "Modem configuration question- what's TTY?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by pollywog on 2007-07-31
Hello All- Ok so I'm trying to set up my modem so that I can send and receive faxes. I went to Synaptic and  I'm trying to install pretty much everything related to mgetty, plus a few other packages that looked like they might be helpful. As the package "lprfax" is installing the terminal asks me to "input serial device for fax printing (eg tty50)". I'm at a loss to figure out what to respond. I went to device manager, but I can't make heads or tails of the info there other than LtWinModem. On my last unsucessful attempt to get my modem working w/ ubuntu all of the programs I was using asked me questions (like which ports I needed to use) that I didn't know the answers to. Faxes seem to be going the way of the dinsaurs, so I'd rather not buy more a Fax machine to do what I should be able to get my present hardware to do. If anyone could give me some pointers here, or explain what tty is I sure would appreciate it- P.W.

---

### Post by crazypiglady on 2007-08-01
You can find out your modem port if you go to system / networking / modem connection / properties, then click on the modem tab there is an autodetect button. If your modem is plugged in and switched on, this will tell you the port its connected to, most likely dev/ttyS0 (would be COM1 in Windows)

good luck

---

### Post by crazypiglady on 2007-08-01
Actually I noticed you said “LtWinModem” I guess this is an internal winmodem (rather than an external beepy lit-up one). Have you configured this to work with Linux?
There is information regarding support for Linux on [www.linmodems.org](www.linmodems.org) and  [http://www.modemsite.com/56k/ltwin3.asp](http://www.modemsite.com/56k/ltwin3.asp) but I find it easier to use an external one.

---

### Post by pollywog on 2007-08-01
Thanks CrazyPig, Great Info on those links. I'll give it a try.

---

