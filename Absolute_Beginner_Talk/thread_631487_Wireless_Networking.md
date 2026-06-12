---
title: "Wireless Networking ?"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by CasPol on 2007-12-04
Hi there;

I have successfully installed Ubuntu 7.10 a few days ago and have almost everything up and running except my wireless net working.

I have the following hardware at my disposal in my laptop:
Broadcom 802.11g Network Adapter

I also use  a Netgear DG 834PN pn modem/router.

I was hoping someone could help with a clear step by step way of getting me wireless to work with Ubuntu so I can surf and mail ..etc ...

Many thanks

---

### Post by rmalouin on 2007-12-04
While mine worked out of the box, I saw this it may help you:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by CasPol on 2007-12-05
Thanks for that link seems like that might help me but what does all this mean :

"sudo apt-get

sudo apt-get install wpasupplicant

sudo apt-get install network-manager-gnome network-manager

sudo gedit /etc/network/interfaces

Comment out everything other than “lo” entries in that file and save the file

Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file

sudo touch /etc/default/wpasupplicant

Reboot your system or use the following command

sudo /etc/init.d/dbus restart

Once you login back in to your machine you need to left-click the network manager icon in Gnome and select your wireless network It should prompts for password, type, etc and It will ask you to choose a password for your new “keyring”.
" 

????????

---

### Post by GSF1200S on 2007-12-05
> **CasPol said:**
> Thanks for that link seems like that might help me but what does all this mean :

"sudo apt-get

sudo apt-get install wpasupplicant

sudo apt-get install network-manager-gnome network-manager

sudo gedit /etc/network/interfaces

Comment out everything other than “lo” entries in that file and save the file

Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file

sudo touch /etc/default/wpasupplicant

Reboot your system or use the following command

sudo /etc/init.d/dbus restart

Once you login back in to your machine you need to left-click the network manager icon in Gnome and select your wireless network It should prompts for password, type, etc and It will ask you to choose a password for your new “keyring”.
" 

????????

Lets start out easy.. please post the results of the following commands in a terminal (terminal is available in system tools)

```
iwlist scanning
```
and
```
iwconfig
```
as well as
```
ifconfig
```

Im just trying to see where your system is at. I know broadcom cards now have an open source driver using the restricted drivers manager, so im not sure if you already have the drivers installed...

---

### Post by CasPol on 2007-12-07
HI GSF 1200

It does not co,e back with anything at all but the prompt in the terminal window.

---

### Post by GSF1200S on 2007-12-07
> **CasPol said:**
> HI GSF 1200

It does not co,e back with anything at all but the prompt in the terminal window.

After you do the ifup ifdown commands, what does iwlist scanning return? It will either return no scan results or give you a listing of networks in the area...

---

### Post by CasPol on 2007-12-14
Hi there;

I have tried all the commands suggested here, but to no avail. It seems to me that no harware is detected at all, though a broadcom card is there and up and running in XP with win.sys driver...

Where to take this next ?

Many thanks...

---

