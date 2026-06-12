---
title: "How to install LAMP with 6.06"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by liangtp on 2006-07-14
Hi,
I just got my 6.06 CDs 2 days ago. I read somewhere that 6.06 comes with option to have LAMP installed automatically if you choose SERVER installation. How and where do i select the option?  When I put in the CD and reboot the system there is no instant where I am provided the option to choose SERVER. It just goes on installation...
Thanks

---

### Post by tribaal on 2006-07-14
Are you sure you got a server install CD? The server version of ubuntu comes on a specific CD...
You can download it [here]("http://www.ubuntu.com/download") :)

I suggest you use bittorrent, it's much faster than regular downloads.

Make sure you get the server .iso file, and burn it to a disk. When you boot using this disk you will have an option labeled "install a LAMP server".

From there on... it's all pretty straigthforward... :)

- trib'

---

### Post by az on 2006-07-14
> **liangtp said:**
> Hi,
I just got my 6.06 CDs 2 days ago. 

If you got them from Shipit, they are the Desktop cds.  They run a live session and can install a desktop system.

A "server" install is an ubuntu base system without the desktop.  You need either the server cd (base install or base with LAMP) or the alternate (Desktop or base install) cd for that.

From any installation (desktop, server, Alternate cd install), you can install the LAMP stack by installing the 

apache2 php5-mysql libapache2-mod-php5 mysql-server

packages.

---

