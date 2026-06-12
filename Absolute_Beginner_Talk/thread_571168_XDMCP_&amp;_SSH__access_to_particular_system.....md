---
title: "XDMCP &amp; SSH  access to particular system...."
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-10-09
my os is ubuntu 7.04 (Feisty)

How can i give XDMCP & SSH access to one particular IP Address in LAN ...

now i enabled System->Administration->Login Window  & Enabled remote Login (Same as Local)

so everyone in our LAN can use my system (if they know my password )

I want to protect this .
I want to Enable XDMCP to a particular IP Address only.


any help please   ......

thank you

---

### Post by bodhi.zazen on 2007-10-09
I would tunnel vnc over ssh ...

You can configure ssh to allow connections only from you (by user name) , use a key, etc ...

[uwiki]VNCOverSSH[/uwiki]

[uwiki]AdvancedOpenSSH[/uwiki]

You can also look into FreeNX

[uwiki]FreeNX[/uwiki]

---

### Post by mokkai on 2007-10-09
i want importantly  about XDMCP connection.....
how to allow to particular IP Address only in LAN (in XDMCP login as local)

---

### Post by bodhi.zazen on 2007-10-09
> **mokkai said:**
> i want importantly  about XDMCP connection.....
how to allow to particular IP Address only in LAN (in XDMCP login as local)

I do not think you can do that, XDMCP over ssh, so XDMCP remains an insecure connection.

To configure your connection to allow connection form only a single IP address, you will need to configure IP Tables. You can do this with Firestarter, and configure firestarter to allow only 1 (or more) ip addresses to connect.

XDMCP uses UDP port 177 and TCP port 6000.

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

[http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

