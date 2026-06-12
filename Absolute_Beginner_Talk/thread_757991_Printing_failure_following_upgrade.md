---
title: "Printing failure following upgrade"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by bwallum on 2008-04-17
I have just lost network printing with latest Hardy update (Printer may not be connected) Updated midday GMT Thursday 17th April.

Any ideas?

---

### Post by quirks on 2008-04-17
Hi bwallum,

can you give us some more details, please? Are you trying to print with your Ubuntu PC to some printer on the network, or are other computers on the network unable to print to a printer connected to your Ubuntu PC? And what do you mean by "Printer may not be connected"?

quirks

---

### Post by bwallum on 2008-04-17
I have been trying to print to a network printer. All worked well until an upgrade today. I have repeated the problem on two other networked PCs. They can't connect to the printer now. On each occasion this happened after updating. My pc is a 64AMD Hardy -16. The other two are 32bit, one AMD Athlon XP cpu,  the other Intel P4 cpu.

Did cups change? Has networking changed? Something has and I do not know where to start looking. All settings in System>Administration>Printing appear the same. i fiddled a lot with one computer, reloading ppd driver etc, but no connection.

Can I ls something to get a better insight?

---

### Post by bwallum on 2008-04-17
Please stand this query down.

I have dusted off a XP machine and get the same problem. i now think it is printer related rather than Ubuntu. The updates were co-incidental I now think.

---

### Post by stevonz on 2008-06-18
Hi I'm having the same problem on Heron since 17 April updates, other networked machines (XP and OSX) work fine with our USB printer connected to an apple airport hub but the Ubuntu machine has stopped printing and says "Not connected?" and gives an error -9.

---

### Post by Ubuntu Warrior on 2008-06-18
Not sure if this is related but we used to print through CUPS from Feisty clients just fine (7.04 server hosting the CUPS). Now, after running the latest updates, CUPS comes up with "quota limit reached" error. Restarting CUPS doesn't resolve the issue.

Anyone know of any problems with the latest CUPS updates for 7.04?

---

### Post by stevonz on 2008-06-21
Found the source of our problems, moblock was blocking all requests through the network to the printer. we could connect to other networked machines fine but just couldn't print. Uninstalled moBlock and all is fine again.

---

