---
title: "Server question"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by gogira on 2007-06-26
How can I access files on my xubuntu machine while travelling? 

I have xubuntu/samba/cups running as a file/print server attached to my home network. I will be away for three weeks and would like to have access to some files while away.

I have read tutorials on setting up LAMP servers but I'm not sure thats what I need, seems a bit overkill. I am very new to linux, so any help would be appreciated.

Thanks

---

### Post by cmnorton on 2007-06-26
First, how will you access your server from outside? Will you need VPN access? 

Second, set up samba. Doing that should add something like the following to /etc/services

netbios-ns	137/tcp				# NETBIOS Name Service
netbios-ns	137/udp
netbios-dgm	138/tcp				# NETBIOS Datagram Service
netbios-dgm	138/udp
netbios-ssn	139/tcp				# NETBIOS session service
netbios-ssn	139/udp

---

### Post by gogira on 2007-06-26
I'm not sure exactly what I need, just a secure way to access files while away. Samba is already setup and the netbios configuration is in /etc/services.

Not sure how to configure those to allow access.

---

### Post by scxtt on 2007-06-26
you need to know your WAN IP (the cable modem IP) and you can ssh (secure shell) to it from anywhere else (provided your forward port 22 to the internal IP of the box you want to use) ...

---

### Post by Wardazo on 2007-06-26
Hi

I'd second the use of SSH. Very secure if you use a good password.

However, you may well have a dynamic ip address in which case it could change during your travels. A good solution here is to set up a dyndns account, and use that to identify the ssh server.

Also if you are partial to gui's you can use most modern ftp clients in sftp mode to transport files about... this comes with the ssh server. 

For command line access use ssh comand in Linux and putty.exe in windows

The ssh server (apt-get install ssh) is pretty secure out of the box but I'd edit the config file to disallow protocol 1.

If you decide on ssh adn you have any problems installing it post back. Good luck.

---

### Post by lazyart on 2007-06-26
I use [hamachi]("http://www.hamachi.cc").  Install the client on your machines (windows version comes with a gui, for linux grab ghamachi as a frontend), create a virtual network and add the machines to it.   Before you head out be sure it's running on your machines and that you can see them.  When on the road, fire it up and you'll have access just like if you were at home.  It's really that easy to do.

---

### Post by gogira on 2007-06-27
Thanks for the replies. I got hamachi setup and working in no time, it will definitely make travelling a lot easier. Good thing is I didn't have to change any existing network settings so my wife can still file/print share.

Thanks.

---

