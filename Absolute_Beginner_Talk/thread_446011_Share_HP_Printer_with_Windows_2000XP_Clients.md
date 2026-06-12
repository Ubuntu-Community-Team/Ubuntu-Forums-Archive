---
title: "Share HP Printer with Windows 2000/XP Clients"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by aaron_summer on 2007-05-16
Good Day Everyone,

I am absolutly new to Linux and thought I was doing so good, until I needed to configure printing.

Yesturday I installed Ubuntu Fiesty Fawn Server (with the default LAMP) and ran aptitude to get the kubuntu-desktop.

After I installed my HP Photosmart C3100 Series printer with the HP toolkit in KDE. The printing, scanning and memory card all work perfectly.

My problem is sharing this printer with my Windows 2000 and XP laptops on the same network.

I have read the Ubuntu Docs and nothing is working (I think I am too new to understand). Is anyone able to help me share this printer?

Thanks in advance!

---

### Post by gamer91 on 2007-05-16
It would probably be easier if you put the printer on a windows PC and used the add network printer function - windows doesn't like talking to non windows PC's.

---

### Post by aaron_summer on 2007-05-16
Unfortunatly I need to have the Linux box act as a print server, as all my other computers are laptops.

Is there any newbie guide that walks through the process?

---

### Post by aaron_summer on 2007-05-17
Nevermind ... I was able to get it working with my Win 2000 Laptop. I uncommented the CUPS printing settings in samba.conf and everything is working great!

---

