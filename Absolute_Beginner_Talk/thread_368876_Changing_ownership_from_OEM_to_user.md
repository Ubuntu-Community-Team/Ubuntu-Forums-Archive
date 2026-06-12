---
title: "Changing ownership from OEM to user"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by maxding on 2007-02-23
I have been installing Ubuntu for the last week trying to figure out why i wasn't the owner.  It was only until recently did someone enlighten me to the fact that when i installed Ubuntu under OEM that this would create problems for me can someone please help me get ownership of my computer without another install.  During the installing i was prompted to use the sudo command to get ownership but being completely new to UBuntu and linux im not sure on how to do that.  Thanks for all the help so far.


Max

---

### Post by taurus on 2007-02-23
Log in with oem as your username and the same password that you've created.  Then run

```
sudo oem-config-prepare
```
to create an actual account for yourself that you will use from now on.

---

### Post by maxding on 2007-02-23
that got rid of the OEM user but i still don't have ownsership to change permissions. 

Max

---

### Post by taurus on 2007-02-23
What permissions do you want to change?  Be real careful what you intend to change because if you change something you are not supposed to, you could crash your machine.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by maxding on 2007-02-23
i want to run /etc/apache2/apache2.conf, however i have tried to change this file but cannot gain access.  I'm sure there is some command which i don't know that will allow me to fully setup my apache server.

---

### Post by taurus on 2007-02-23
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apache2/apache2.conf
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by balbir97 on 2007-02-27
Hi!!.

press: alt +F2,

then type: gksudo nautilus

now you will get root window

hope u are using GNOME

:KS

---

