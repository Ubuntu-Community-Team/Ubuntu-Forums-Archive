---
title: "Network printing"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by nrpgeek on 2007-07-19
Can anyone help me print to a networked printer?
It's a HP 4100 LaserJet connected to a Windows 2000 computer on a peer to peer Windows network. (All the other Windows machines print from it)

According to all the documentation HP printers are well supported in Linux in general and Ubuntu has the drivers (The model is listed in the install printer wizard!)

I've tried every conceivable network address (IP address, network name, etc), I've even tried navigating to the PC using file browser then copying and pasting the address from there.

Similar with all the options for CUPS, Windows, JetDirect...

I've been using Ubuntu for two weeks now and love it - I've never used Linux before, though I have 20 Years in computers.

I've shared drives and groups using Samba, I have an intranet  server running on LAMP all by reading the usually excellent documentation...
...but I can't install a *&^*&%&* printer!

---

### Post by ihristov on 2007-07-19
Several questions:

Does this printer have a network interface? Do you know it's IP address? Can you open the web interface of the printer if it has one?

It is not clear if the other Windows computers are printing to the printer directly (i.e. the printer is connected directly to the network and has it's own IP address) or via a shared printer (i.e. the printer is connected via USB or parallel cable to one of the PC's and all the other PC's are configured to use the printer that the "print server" PC is sharing)

---

### Post by nrpgeek on 2007-07-19
The printer is connected via parallel port & shared via windows file & printer sharing. All the pc's print to it via peer to peer network.

---

### Post by ihristov on 2007-07-19
In this case you want to use Samba.

1. Are you able to open a shared folder on the Windows print server from the Ubuntu box?

2. What is the exact URL of the printer in Windows you mention in the first post?
Isn't it something like \\computer\printer

3. Not sure if it's relevant, but you might need to pay attention to capitalization in the URL. Everything in Linux is case-sensitive.

---

### Post by nrpgeek on 2007-07-21
Sorted!

In the printers window select "Global Settings&#8221; and then &#8220;Detect LAN Printers". This is disabled by default for security reasons.
You can then navigate to the printer you want to add, select the driver and install it as a network printer -  so easy when you know how!

Remember to turn "Detect Lan Printers" back off when you've finished though  - to close the security loophoe.

---

### Post by ihristov on 2007-07-21
Indeed, extremely simple once you know it.
I do not recall having to do that when I installed my network enabled HL-2070N Brother. Maybe because it's not shared via Samba, but it's a "native" network printer and I think uses the IPP protocol (port 631 I think)

---

### Post by nrpgeek on 2007-07-21
All's well that ends well as they say. Thanks for all the help - it's appreciated!

---

