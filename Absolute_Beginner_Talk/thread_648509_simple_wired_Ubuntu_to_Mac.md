---
title: "simple wired Ubuntu to Mac"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by cortical on 2007-12-23
Hi All,

I have an old 500 MHz pc that I want to use for testing Linux, and networking in general.
In the last week, have booted from Knoppix (on the pc and under Mac Parallels interestingly), installed Ubuntu Server, Xubuntu, and Ubuntu on the pc box ; runs only Ubuntu currently.

I have a mac connected to a Ubuntu box. With a manually configred IP,  can get each to ping the other, but not actually mount either volume



how to test the most simple scenario: wired NIc to NIC
To connect a Mac OSX.4.11 to Ubuntu 7.10
physical connection: cat5 crossover cable
PCI Adapter: Wise Fast Ethernet 10/100M Adapter (Realtec based; no other info)
Link LED on, 

MAC
Apple Menu; System Preferences; Network
New Location
Show:		Built in Ethernet
TCP/IP tab: 
Configure IPv4:	manually
I{ Address:	10.10.10.1
Subnet Mask:	255.255.255.0


LINUX
Network Settings
Connections; Wired Connection; Properties
Configuration	Static IP Address
IP Address	10.10.10.2
Subnet Mask	255.255.255.0

How do I get a volume to mount?

---

### Post by blueridgedog on 2007-12-23
Not speaking from the mac side, you need to have some form of software on the OS that "shares" a volume.  For Linux, that is samba.  So the next logical step is to be certain that samba is installed on ubuntu, running and configured (via editing /etc/samba/smb.conf).

But, before you embark on that endevor, you should read up on samba:

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)

Then I suggest your read up on mounting remote samba shares with a mac.

I would also put the name of the mac in /etc/hosts so you could ping by name and do the same on the mac side (I have no idea how).

You have created a great lab, but you will need to tinker for a big.  Start with samba.

---

### Post by cortical on 2007-12-23
thanks brd, had read extensively but samba was a 'avoid this' issue in what I had read. Will pursue it from your suggestion, thanks indeed.

regards

Chris

---

### Post by wormser on 2007-12-23
The easy way and more secure way is to use ssh.  Places> Connect to Server> Service type: ssh> and enter in the rest of the information needed.  If the user name is different on the Mac then under Server: put username@ipaddress.

---

### Post by blueridgedog on 2007-12-23
The OP wanted to mount a volume from one machine to another.

---

