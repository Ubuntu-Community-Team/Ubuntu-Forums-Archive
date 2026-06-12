---
title: "A few simple problems..."
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by TidusBlade on 2007-10-12
Well I got everything working till now, just puzzled at a few problems :S 
I tried many things but my internet seems to not start on startup sometimes, Im using a Belkin Router through a LAN cable if that helps.... 
When I log out of root account, I see the cursor but the screens just black so I cant do anything so I have to reboot :S
And I recently installed a package called "winefix", I have no idea why I cannot remove it, even if Im logged in as root, returns me this error:
```
root@blayde:/home/watermelon# sudo dpkg -r winefix
(Reading database ... 138437 files and directories currently installed.)
Removing winefix ...
update-mime-database: I don't have write permission on /usr/local/share/mime.
Try rerunning me as root.

Aborted (core dumped)
dpkg: error processing winefix (--remove):
 subprocess pre-removal script returned error exit status 134
+ [ ! -f /etc/gnome/defaults.list.bak ]
+ [ -f /etc/gnome/defaults.list ]
+ cp /etc/gnome/defaults.list /etc/gnome/defaults.list.bak
+ grep -o -m 1 winefix /etc/gnome/defaults.list
+ match=
+ [  != winefix ]
+ echo application/x-ms-dos-executable=winefix.desktop
application/x-extension-lnk=winefix.desktop
application/x-extension-msi=winefix.desktop
+ tee -a /etc/gnome/defaults.list
application/x-ms-dos-executable=winefix.desktop
application/x-extension-lnk=winefix.desktop
application/x-extension-msi=winefix.desktop
+ gtk-update-icon-cache /usr/share/icons/gnome
+ update-mime-database /usr/share/mime/
+ update-mime-database /usr/local/share/mime
update-mime-database: I don't have write permission on /usr/local/share/mime.
Try rerunning me as root.

Aborted (core dumped)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
 winefix

```
I did try a few things on the root account but I didnt go any further, last time I tried to mess around with things, I had to reinstall Ubuntu :P
Any help would be greatly appreciated ;)

---

### Post by kidrock_linux on 2007-10-12
First I think that the root account must not be used! 
Use instead the command "sudo" . 


To unistalling winefix you tryed :

```
sudo apt-get remove winefix
```
Post the output of this command.

Also you could do this throught synaptic.

About the internet connection: give more information such as configuration file (/etc/network/interfaces), ip address (static or dhcp ). Do you use network manager to manage the connection?

---

### Post by TidusBlade on 2007-10-12
I know I shouldn't be using that account, but sudo wasent working before and using root worked once, so I tried it again, not this time though... 
It wouldn't remove through Synaptic , I tried :( Trying to uninstall it from Synaptic gives this:
```
E: winefix: subprocess pre-removal script returned error exit status 134
```
Anyways I tried sudo apt-get remove winefix  and got this: it still didnt remove itself...
```
watermelon@blayde:~$ sudo apt-get remove winefix
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mplayer-skins bittornado libsqlite0 libgtk-jni libcairo-java libggi2 libgii1
  libglib-java libgii1-target-x libswt3.2-gtk-jni liblame0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  winefix
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 262kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 138437 files and directories currently installed.)
Removing winefix ...
update-mime-database: I don't have write permission on /usr/local/share/mime.
Try rerunning me as root.

Aborted (core dumped)
dpkg: error processing winefix (--remove):
 subprocess pre-removal script returned error exit status 134
+ [ ! -f /etc/gnome/defaults.list.bak ]
+ [ -f /etc/gnome/defaults.list ]
+ cp /etc/gnome/defaults.list /etc/gnome/defaults.list.bak
+ grep -o -m 1 winefix /etc/gnome/defaults.list
+ match=
+ [  != winefix ]
+ echo application/x-ms-dos-executable=winefix.desktop
application/x-extension-lnk=winefix.desktop
application/x-extension-msi=winefix.desktop
+ tee -a /etc/gnome/defaults.list
application/x-ms-dos-executable=winefix.desktop
application/x-extension-lnk=winefix.desktop
application/x-extension-msi=winefix.desktop
+ gtk-update-icon-cache /usr/share/icons/gnome
+ update-mime-database /usr/share/mime/
+ update-mime-database /usr/local/share/mime__________________
update-mime-database: I don't have write permission on /usr/local/share/mime.
Try rerunning me as root.

Aborted (core dumped)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
 winefix
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp





iface ppp0 inet ppp
provider ppp0









auto eth0
```
And I havent changed anything about the internet, too scared to screw it up like last time :S Ending in a reinstallation :P But im pretty sure im DHCP.
Thanx ;)

---

### Post by kidrock_linux on 2007-10-14
The first problem I think you could look about the permission of that file where apt-get stop (/usr/share/mime). 

Open a terminal and try:

```
cd /usr/local/share
```

and then:

```
ls -n | grep mime
```

and post here the output.

About the internet connection I have to know how router is configured. So I need to know the ip address of the router and also post the contents of another file, /etc/resolve.conf which contain the dns ip address.

---

