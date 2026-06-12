---
title: "Ping + names server"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by naga123 on 2005-10-04
I cannot **ping** the pcs in Lan using 
**ping <host name>**
I wanna know whether I can use **ping** command using **wins server**??
plz help me.

---

### Post by KingBahamut on 2005-10-04
Local DNS Issue sounds like. Are you getting your local IP via DHCP or Static? Whats in your resolv.conf file? hosts file check ok?

---

### Post by mlomker on 2005-10-04
You either have to add all of your local machines to the /etc/hosts file or have them configured in a local DNS server.

Is this a home network or a Windows LAN?  I have a Windows network at the office but we run Microsoft's DNS server, so that solves my problem.

---

### Post by naga123 on 2005-10-06
I can ping using
**ping <IP address>**
but not by hostname.

---

### Post by mlomker on 2005-10-06
[QUOTE=naga123]I can ping using
**ping <IP address>**
but not by hostname.[/QUOTE]

Yes, you'll need to add the hostnames and IP addresses to the hosts file.  If you have any questions about doing that then post your files and we'll take a look.

---

### Post by naga123 on 2005-10-07
**there r more than 100 pcs in my lan**. I think more than **100 entries** in  **/etc/hosts** file is not a good solution.

A wins server is assigned.

I dont have any problem in **windows** when  **accessing shares** using pc names.
But I dont know why this is with **linux**.

---

### Post by mlomker on 2005-10-07
[QUOTE=naga123]**there r more than 100 pcs in my lan**. I think more than **100 entries** in  **/etc/hosts** file is not a good solution.
[/quote]

You're right, that's too many but you didn't mention that.  From a network admin standpoint I'd recommend installing a Microsoft DNS server and integrating it with WINS (that's what I do at my office).

EDIT:  Okay, I spent a couple hours looking at this.  If you **gksudo gedit /etc/samba/smb.conf** and add the following line then name resolution will work when you are using SMB mount and within file managers (assuming that your DHCP server is dishing out the WINS entries):

```

include = /etc/SAMBA/dhcp.conf

```

This **will not** allow the ping command to function, though.  You have to install a DNS server for generic TCP/IP tools such as ping to work.

---

