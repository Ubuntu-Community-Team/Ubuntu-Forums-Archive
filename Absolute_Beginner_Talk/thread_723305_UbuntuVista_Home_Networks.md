---
title: "Ubuntu/Vista Home Networks"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by dogdog on 2008-03-13
I am an experienced Windows user but new to Linux.
I have a Dell PC with Windows Vista Ultimate as the operating system. I have a second older Dell PC on which I have just installed Ubuntu (v 7.10) – Ubuntu installation via downloaded image for alternate installation disk (I only have 128MB of RAM on older PC).
I am trying to set up a home network with these two PC’s. I have a cable modem to a wired Linksys Router with the 2 PC’s connected to router. In particular I want to see the ubuntu PC from the Vista PC and transfer files from Vista PC to Ubuntu PC. However, I am having problems despite following instructions that I have found.
So far on the Ubuntu PC I have:
1.	Created a new folder and activated file sharing for that folder. I installed Windows Network Support (SMB) – but did not install Unix Network Support (NFS). The sharing is through SMB and I have removed the tick from the read only box.
2.	I have installed Samba via the add/remove programs box.  Then via Terminal  I have set Samba password (sudo smbpasswd –a [user name]) and set Samba to enable user name (sudo smbpasswd –L –e [user name].
3.	Opened Samba via  System-Admin-Samba. Then under Preferences-Server Settings-Basic have set workgroup name to be the same as workgroup name on Vista PC. Under Preferences-Server Settings-Security the settings are: Authentication Mode=Share, Encrypt Passwords=Yes, Guest Account=[user name].
4.	I have not installed Samba onto Vista PC; I assume that Vista functionality is sufficient.
5.	Under System-Admin-Network then Network Settings-General: Host Name=ubuntu, domain=workgroup name.
When I tried to ping ubuntu Pc from Vista PC got no response. Then used Firestarter to configure ubuntu firewall; Under Firestarter ubuntu policy-Inbound Traffic, in Allow Connections from Host I have entered IP address of Vista PC. However I am still getting no response when I try to ping ubuntu PC from Vista PC.
When I look under Networks in Vista I see the ubuntu PC but when I try to access the ubuntu PC I get the message “Windows cannot access \\UBUNTU “ and Vista cannot diagnose a solution.
Now stuck!! And would appreciate any help.

---

### Post by (((X))) on 2008-03-13
Samba emulates windows network environment, so no need to install samba on Vista.

Take a look at 
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

Looks like this guy is familiar with  firestarter
[http://www.youtube.com/watch?v=MAQbGJOfWh4](http://www.youtube.com/watch?v=MAQbGJOfWh4)

---

### Post by Mauler5858 on 2008-03-13
You need to edit the samba config file with a text editor(at work and i forgot name and path).  There are two lines that should show something like:

; readable=no
; editable=no

or something like that. Change them to:

readable=yes
editable=yes

and make sure you take the semicolon out of it to uncomment the line.

---

### Post by dogdog on 2008-03-13
I will try these suggestions tomorrow.

Do not understand why nobody mentions configuration of firewalls both on ubuntu and vista?? If I cannot ping ubuntu PC from Vista PC surely this indicates a very fundamental problem??

---

### Post by (((X))) on 2008-03-14
Iptables configuration to allow ping:
[http://www.cyberciti.biz/tips/linux-iptables-9-allow-icmp-ping.html](http://www.cyberciti.biz/tips/linux-iptables-9-allow-icmp-ping.html)

---

### Post by njparton on 2008-03-14
If you're connecting via router you may need to forward sambas ports to each of the computers.  Google for them.

There should be no need to dabble with iptables but you may need to tweak windows firewall if you use it.  I have a similar setup to you and as I'm behind a router I don't use windows firewall at all.

---

