---
title: "Driver issue HP D2300"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by stoppage on 2008-03-21
I have a question on the driver for a HP deskjet D2300 printer. Currently under „system/admin/printer“ I'm on basic (recommended) driver hpijs eveen though Synaptec says hplip is installed. I'd like the functionality of ink level, so if hplip is already installed why isn't printer using same and will I mess up a functioning printer by changing driver ? Can anybody help me out here please?

---

### Post by linuxwizard on 2008-03-21
HPIJS is part of the HPLIP package. To check ink level in terminal type > hp-levels
I would suggest using the HP toolbox more options & settings > in terminal type > hp-toolbox

---

### Post by stoppage on 2008-03-21
Prob. is I dont have a toolbox. When I install python-qt3 as per.....[https://lists.ubuntu.com/archives/ubuntu-bugs/2007-March/444739.html](https://lists.ubuntu.com/archives/ubuntu-bugs/2007-March/444739.html).... the printer isn't even recognised (by instruction hp-toolbox). I'm missing something else here...

tony@youhits:~$ /usr/bin/hp-toolbox


HP Linux Imaging and Printing System (ver. 1.7.3)

HP Device Manager ver. 9.0
...

...X Error: BadDevice, invalid or uninitialized input device 166

  Major opcode:  146

  Minor opcode:  3

  Resource id:  0x0

Failed to open device

X Error: BadDevice, invalid or uninitialized input device 166

  Major opcode:  146

  Minor opcode:  3

  Resource id:  0x0

Failed to open device
....
Any ideas please?

---

### Post by linuxwizard on 2008-03-21
You will have to Add your printer to the Toolbox. In terminal > hp-toolbox

NOT > /usr/bin/hp-toolbox

---

### Post by stoppage on 2008-03-23
Both „hp-toolbox“ and „/usr/bin/hp-toolbox“ yield same results but install of printer in toolbox does the trick.....funny old Feisty!
Obliged

---

### Post by linuxwizard on 2008-03-23
Well I take it that you have everything setup and you can check your ink levels. Please mark thread as SOLVED > [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

