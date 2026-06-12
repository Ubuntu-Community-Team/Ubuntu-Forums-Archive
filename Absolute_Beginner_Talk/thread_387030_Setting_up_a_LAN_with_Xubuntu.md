---
title: "Setting up a LAN with Xubuntu"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by AMorris on 2007-03-17
I know this is a very basic question and I probably won't include enough details but I'm a real Linux newbie.  How do I join a LAN with Xubuntu.  I can get into the Network Settings btu after that I have no idea.  Is it supposed to automatically detect a LAN or do I have to configure it manually?

---

### Post by dstew on 2007-03-17
What kind of LAN do you have? Xubuntu should detect your network card all right, but you will probably have to do some configuration to use the network. If you want to share files or printers with Windows PC's, you have to install Samba. TCP/IP is installed by default, so to connect to the internet throught a router on the network is easier.

---

### Post by AMorris on 2007-03-17
I have an ethernet LAN (wired) if thats what your asking.  I am connected to the Internet through an ADSL modem connected to the Wireless/Ethernet Router.  All the other computers on the network are running WinXP so I understand that I won't be able to share documents without Samba, but will I be able to connect to the Internet.

Should I select DHCP or Static IP Config in the menu for Wired connection?  Do I have to change the Host and Domain names?

---

### Post by dstew on 2007-03-18
If your network router is set up to do DHCP, then do that. If DHCP is disabled, you need to use static IP. Your host and domain names don't need to be changed to use the internet, nor to share files. To share files, you just need to know your host name.

---

