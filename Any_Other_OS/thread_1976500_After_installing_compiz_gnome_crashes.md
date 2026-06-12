---
title: "After installing compiz gnome crashes"
date: 2012-05-08
forum: Any Other OS
---

### Post by Fwission on 2012-05-08
So any ideas, here is my .xession-errors file dump

```
/etc/gdm3/Xsession: Beginning session setup...
localuser:daniel being added to access control list
/usr/bin/startxfce4: X server already running on display :0
ssh-agent is already running
xfdesktop[5081]: starting up
Initializing tracker-store...
xfce4-settings-helper: Another instance is already running. Leaving...
Tracker-Message: Setting up monitor for changes to config file:'/home/daniel/.config/tracker/tracker-store.cfg'
Tracker-Message: Setting up monitor for changes to config file:'/home/daniel/.config/tracker/tracker-store.cfg'
Starting log:
  File:'/home/daniel/.local/share/tracker/tracker-store.log'
Initializing tracker-miner-fs...
Tracker-Message: Setting up monitor for changes to config file:'/home/daniel/.config/tracker/tracker-miner-fs.cfg'
Starting log:
  File:'/home/daniel/.local/share/tracker/tracker-miner-fs.log'
unhandled event type: 33
unhandled event type: 33
env: synaptic: No such file or directory
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-nAZB43/pkcs11: No such file or directory
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-nAZB43/pkcs11: No such file or directory
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
BrlAPI exception: Invalid parameter on Write request of size 26 (66 00 00 00 00 00 00 01 00 00 00 00 00 00 00 00)
You may wish to add the -ldebug option to the brltty command line in order to get additional information in the system log

(tracker-miner-fs:5114): Tracker-WARNING **: Couldn't properly parse desktop file 'file:///usr/share/applications/brasero-nautilus.desktop': 'Desktop file doesn't contain type'
```

Any ideas, I'm on xfce right now and uninstalled compiz

---

### Post by wilee-nilee on 2012-05-08
So really you are missing some details here. The install release and a hardware list. Also the unity desktop is a plugin in compiz, both are part of gnome 3. If you are running at the lowest release 11.10 up to 12.04 install the gnome 3 desktop if you like it is rather nice and does not use compiz but mutter as a manager. The gnome shell also gives you the gnome 2 "like" fall back desktop.

gnome 3 install.

```
sudo apt-get install gnome shell
```For a hardware listing, at least most, so you can post it.

```
lspci
```So be careful about just removing apps unless you know exactly what you're doing, and save the list of removed packages in case a reinstall is needed.

Details are really important here so we know exactly what you have done and what you have done it to (the computer) lol. :)

---

