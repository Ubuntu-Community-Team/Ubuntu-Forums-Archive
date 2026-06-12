---
title: "Need Help installing applications."
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Dr.Suse on 2007-12-08
ok, ive tried everything and i dont know what to do. sudo apt-get install never seems to work:
```
cobin@laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
cobin@laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
cobin@laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine
cobin@laptop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

and the Add/Remove Applications feature doesnt work because it sends me through an endless loop. whenever a checkmark or double click an application it says the list is not availible and it apparently downloads a list and when i double click one, it says the list is not availible etc.

and whenever i load [this URL]("http://packages.ubuntu.com/gutsy/web/flashplugin-nonfree") my screen blinks and it takes me to the login screen. 

AND when i try to enable the restricted drivers through the daemon, it tells me to insert the cd and it doesnt help me at all, it doesnt try to download the driver instead,

im really lost for words and ideas. im new to linux and xubuntu is my first distribution.

does anyone have any ideas?

---

### Post by forestpixie on 2007-12-08
can you do this in terminal and post your sources

```
cat /etc/apt/sources.list
```

---

