---
title: "installing samba and nfs for file sharing"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by steeveepee33 on 2007-01-13
Hi, this is my first day with Ubuntu, and with any other Linux OS for that matter. I have Ubuntu 6.10 installed, and I am on a home network consisting of a cable modem, with a soho router attached, and two computers running off the router. One computer is a windows XP home, and the other is my Ubuntu workstation. I am interested in finding out how to share files between the two computers. I tried to create a shared folder in my Ubuntu desktop, but it said I need to install Samba, and/or NFS. I clicked the option to have them both installed with no success. How can I get this done so that I can begin sharing files between the two computers? And is this all I need to do? Thank you in advance.:-k

---

### Post by tonyr1988 on 2007-01-13
You're best bet is to just use Samba for all sharing (NFS = Linux<->Linux, but Samba = sharing between Linux<->Windows AND Linux<->Linux...make sense?)

As to how to set Samba up, try [this]("https://help.ubuntu.com/community/SettingUpSamba") how-to. It should work in Edgy (6.10), but I'm not positive - I haven't setup Samba yet on my Edgy desktop. If you get stuck at any of the steps, feel free to ask.

---

