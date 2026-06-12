---
title: "Setting Up  Network Lpd Printers"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by cpadwick on 2007-10-25
This is an observation that I made that hopefully may help other users.  I have a ubuntu 64 bit gutsy gibbon box that is connected to an nis server.  I found it impossible to add a network printer while logged in under an NIS account.  I would get through the printing wizard (System->Administration->Printing under gnome) to the last step and then the wizard would ask for a password and wouldn't accept my NIS password.  The wizard gives you no option to run as administrator either.

Fortunately I had first created a local admin account when I set up the box.  I logged in under the admin account and executed the exact same steps and I was able to add a printer successfully.

---

