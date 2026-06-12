---
title: "[SOLVED] Connect to Internet usian Dial Up Modem!!!"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by bahramd on 2008-01-28
I have an DELL INSPIRON 1300/B130 laptop. I recently have installed UBUNTU ver 7.10.  I am trying to install my modem. My Modem is HSF. I have installed the driver "hsfmodem_7.60.00.06oem_i386.deb" which I got from DELL website and as it has instructed I double clicked on the deb file the installation began. Then after entering some path similar to "/lib/firmware/2?????????generic/??????" in the black area below with all the white texts   after that   below the status bar is written  "install is complete"  now I once restart my computer so the driver will recognize the modem. Now can anyone tell me how can I make sure my modem is installed? I have downloaded gnome-ppp but don't know how to install the software and if you are going to suggest about wvdialer also has the same problem so tell me how to install it!!!!!!!!!!!!!
Finally can anyone guide me without installing gnome or wvdialer how can I connect to internet as the instruction in the documantation couldn't help me.

Thank you

---

### Post by spiderbatdad on 2008-01-28
As I understand it, gnome-ppp is a frontend that uses wvdial. You'll want to make sure all other network interfaces are disabled...like eth0, eth1. Then in a terminal```
wvdialconf
``` This will write the /etc/wvdial.conf  file that gnome-ppp will use. You'll need to edit this file to inlude the correct phone number, username, password. You can also configure this info using Gnome-ppp, but the wvdial.conf file will still need some tweaking. 

Also, there is a bug in gnome-ppp for 7.10. You should look for the package called Gnome-pppfixedforgutsy. And install it instead. First:```
sudo apt-get remove --purge gnome-ppp
``` restart you computer and install the fixed package. You'll probably need to do a little research to set wvdial up correctly. Here's an example of mine:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Auto DNS = yes
Modem Type = Analog Modem
Phone = xxxxxxxxxx
ISDN = 0
Username = xxxxxxxxxx
Init1 = ATZ
Password = xxxxxxxx
Carrier Check = no
Stupid Mode = 1
Modem = /dev/ttySL0
Baud = 460800
```

If you dont get the fixed gnome-ppp, this file will have some extra characters at the beginnings of the username password lines...some other files get written incorrectly as well...at least, that's my understanding.

---

### Post by spiderbatdad on 2008-01-28
Also...I have been advised that kppp works much better than gnome-ppp. You can use it in Ubuntu. My experience was, kppp would have been easier to get working, had I been in certain countries where the wizard works. US was not on that list.

---

### Post by spiderbatdad on 2008-01-28
sorry to keep reposting, but I keep thinking of more. You'll need scanModem. Run it and it will create a file called modem that will be valuable to getting things set up for you. Read the files..."Read This First," and "Modem.txt," etc.

---

