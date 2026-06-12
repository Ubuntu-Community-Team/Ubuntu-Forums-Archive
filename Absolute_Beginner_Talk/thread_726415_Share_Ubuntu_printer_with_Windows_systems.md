---
title: "Share Ubuntu printer with Windows systems"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by medley on 2008-03-16
Hi all

I recently decomissioned my XP system that was sharing the locally installed printer with the rest of the household. The printer is now attached to my Kubuntu box, and I want to share it from here with the rest of the network, which are all XP machines.

I did configure it in Samba as best I know how, but the other systems are unable to see the printer.

Here are the contents of /etc/samba/samba.conf

[global]

guest ok = yes
domain master = no
preferred master = no
workgroup = OUR HOUSE
server signing = Auto
security = share
server string = Vostro
local master = no
password server = None
guest account = root
dns proxy = no
restrict anonymous = no
max protocol = NT
acl compatibility = winnt
ldap ssl = No

[share]

path = /
read only = no
create mask = 0777

[Maxtor 300]
path = /media/Maxtor 300
case sensitive = no
strict locking = no
msdfs proxy = no
guest only = yes
read only = no

[Photos]
path = /media/Maxtor 300/Multimedia Files/Photos

[File Transfers]
path = /media/Maxtor 300/xfer
read only = no

[App Installs on Maxtor]
path = /media/Maxtor 300/Application Installs

[Samsung_on_Vostro]
printable = yes
printer name = Samsung_on_Vostro

[Alison's songs]
path = /media/Maxtor 300/Alison's tracks

The file shares are working; the printer is not. Any suggestions?

---

### Post by The Cog on 2008-03-16
[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

No need for samba

---

### Post by tgalati4 on 2008-03-16
In other words, go to a browser:

[http://localhost:631](http://localhost:631)

Add your printer there.

CUPS is the printing system used in Linux.  It can do some cool things.  Spend some time with it and you will see its power.

---

