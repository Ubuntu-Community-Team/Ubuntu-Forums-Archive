---
title: "setting internet connection"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by harys on 2006-03-12
hi, i would appreciate it if anyone could tell me how to set internet connection on ubuntu. thanks a lot. harys

---

### Post by Akli on 2006-03-12
If you have an Adsl connection (lan adls router), do this:

-download this file :

[http://easylinux.info/uploads/rp-pppoe-3.6.tar.gz](http://easylinux.info/uploads/rp-pppoe-3.6.tar.gz)

-restart your computer and login in ubuntu,

-copy the file on your desktop:

applications>>accessories>>Terminal

sudo -s -H
(give your password)
cd Desktop
tar zxvf rp-pppoe-3.6.tar.gz -C /opt/
chown -R root:root /opt/rp-pppoe-3.6/
gedit /usr/share/applications/RP-PPPoE.desktop

    * Insert the following lines into the new file 

[Desktop Entry]
Name=RP-PPPoE
Comment=RP-PPPoE
Exec=gksudo /opt/rp-pppoe-3.6/go-gui
Icon=
Terminal=false
Type=Application
Categories=Application;Network;

    * Save the edited file
    * Read #How to refresh GNOME panel
    * Applications -> Internet -> RP-PPPoE

[http://easylinux.info/wiki/Ubuntu#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29](http://easylinux.info/wiki/Ubuntu#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29)

After launching the RP-PPPoE (you'll be asked to enter your ubuntu password), 

-fill in the username and the password (of the adsl connection) in the "basic" tab,
-switch to the "NIC and DNS" tab, choose your Ethernet interface : eth0 , DNS setup : from server.

click on start and it should be working.

---

### Post by bscbrit on 2006-03-12
Well the easy answer is 'Connect the wires and set the correct values' but I don't think that it will help you very much :D 

Have you got:

1. A dial-up connection or somekind of DSL connection?

2. Some hardware details?

---

### Post by bscbrit on 2006-03-12
Akli - you advice may be useful, but it certainly doesn't apply to every kind of hardware ADSL connection.  Is there another thread which gives more information regarding this particular problem?

---

### Post by Akli on 2006-03-12
[QUOTE=bscbrit]Akli - you advice may be useful, but it certainly doesn't apply to every kind of hardware ADSL connection.  Is there another thread which gives more information regarding this particular problem?[/QUOTE]

Well, I tried this in three different countries with obviously three different modems, sometimes using the 3.6 vesion and sometimes the 3.7.

but you are right, I had the same config in the three cases : a lan adsl router, I have to admit that I don't know how to do it with a usb router.

---

### Post by bscbrit on 2006-03-12
Akli - my own router is a DSL-504.  It configures itself automagically - (well almost) and then the only connections for the computer are ethernet.  Dead easy to set up and simple to keep working.  I also do not need any additional software installed.  As long as there is a working network card, which most modern boards have built in and, if not, cheap NICs are easy to come by, then I can connect to my network. :-D

---

