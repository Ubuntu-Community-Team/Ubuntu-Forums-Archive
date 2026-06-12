---
title: "Ftp server question"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by Sagrath on 2005-11-22
I found a thread were it explains how to install and setup a Ftp server... 

So i've got a locan area network set up at my place with one computer runing Ubuntu and 3 running M$. I would like to share files and excange them through the local network. Now i've had some problems with samba on mandrake so i would like to give it a go with a FTP connection.

How do i make that the FTP is restricted only to LAN (IP adresses like 192.168.0.x) and not to WAN because i dont want anyone accesing the service. And can the LAN users connect to the FTP using my network IP (192.168.0.1) or they have to use my WAN ip? (86.105....)

Many thanx

---

### Post by somody on 2005-11-22
Why would you have an FTP for LAN?  You can just share individual folders/files across the network!  The whole point of an FTP is that it's a File Transfer Protocol for people far away from the host for the sole purpose of retreiving data from said host.

---

### Post by narcolept on 2005-11-22
He did specify that he didn't want to use samba or the like, so that rules out a share pretty much.  To the OP, it should be specified as far as IP restrictions in the config of the ftp server if possible, or the man page. Also, you could do it with IP tables, and just block all traffic to port 21 for ftp, and add an allow rule for the IP of the other machine you'd like to connect with. In the interest of learning a useful tool like IP tables, I'd recommend reading the man page for IPtables by typing 'man iptables' rather than just giving you the commands.  Also, You should note if you're behind a router/switch and don't have port 21 forwarded to the ubuntu box, that outside connections won't hit it anyway. I'd still recommend learning about iptable sthough, they're useful stuff :)

---

### Post by Sagrath on 2005-11-22
i've used samba on mandrake 10.1 but i dont know what went wrong but i was downloading from the network with maxumum  80KBs :o :o  so i thought i did something wrong (didnt handle with samba config files)

so now i would like to try with a FTP server but still i think i could give it a try also with samba...

to install i just need apt get samba ?

---

### Post by narcolept on 2005-11-22
yes, samba should be in the standard repositories. You will need to do some configuring though, so be warned.

---

