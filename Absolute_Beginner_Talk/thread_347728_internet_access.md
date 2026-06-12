---
title: "internet access"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by terb on 2007-01-27
i have a winmodem installed and tried to get a driver from linmodems for it but could not. read in the forum here of a couple of people who had diamond external serial modems and i guess they were working so i bought one. i am dual booting with xp/ubuntu. i diabled the driver on the winmodem and hooked up the ext. modem. it works great with xp but ubuntu does not see it but it does see my winmodem. for the past 3 weeks i have read and read and have not made much progress. i have tried to install gnome ppp but it would not install--anyway-- i read today of something called "SLOMODEMD" which is supposed to do well. my 1st question is does anyone know where to download it?? i have googled it but not found it.
#2 question-- i keep reading of people going thru a router- do you think this would help me?? thanks for your patience

---

### Post by kosmic on 2007-01-27
The Router is the way to go.

1 - Easy to  configure  in Linux, Windows, OSX ...
2 - The routers allways have a firewall
3 - You can share the internet to other computers in a easy way :)

If you dont want to buy a router, instead you can buy an external modem, see in linmodems what are the best suported

---

### Post by ieee488 on 2007-01-27
> **terb said:**
> i have tried to install gnome ppp but it would not install

Can you explain how you exactly tried to do this?

I installed gnome-ppp just fine in Ubuntu 6.06, and it works with both my internal modem (which is Linux-compatible) and with an external modem I bought on eBay.

---

### Post by terb on 2007-01-28
Kosmic-- thanks for the reply -- i do have an external serial modem-- would a router help?
ieee488 thanks for the reply--- i downloaded the gnome ppp with xp and wrote it to a cd but it seems that ubuntu would not read it.

---

### Post by ieee488 on 2007-01-28
Instead of using a CD, do you have a flash drive? I prefer to use that to transfer files from Windows to Ubuntu.

go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  and select Ubuntu version and download gnome-ppp from there

you don't need a router for a serial external modem for dial-up

---

### Post by rccharles on 2007-01-28
> **terb said:**
> wrote it to a cd but it seems that ubuntu would not read it.

Did the cd mount on the desktop?

You could try manually mounting the cd.

cat /etc/fstab

find the name for the cd.  It is probably /media/cdrom0

Place the cd in the drive.

sudo mount /media/cdrom0

enter your logon password.

Depending on the entry in fstab, you could do:

mount /media/cdrom0

Perhaps windows wrote the cd in some format Ubuntu could not understand.  Try writing the cd in iso 9660.


Robert

---

