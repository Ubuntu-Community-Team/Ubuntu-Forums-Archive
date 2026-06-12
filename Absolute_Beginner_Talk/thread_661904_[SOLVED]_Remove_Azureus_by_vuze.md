---
title: "[SOLVED] Remove Azureus by vuze"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-01-08
I have not 1 but 2 copies of Vuze (Azureus) in my Apps/Internet.

I tried sudo apt-get remove azureus

I removed about 8 meg.

I rebooted and it still there!!!!

How does one remove this?

---

### Post by Perfect Storm on 2008-01-08
It could be a ghost link in your menu.


```
whereis azureus
locate azureus
```

---

### Post by Mark_in_Hollywood on 2008-01-08
And files found by those commands can be 'simply' deleted? That is, deleting them won't harm dependencies, other files? Sorry for such a basic question, but Azureus is virgin territory for me.

---

### Post by Perfect Storm on 2008-01-08
What's the output?

---

### Post by Mark_in_Hollywood on 2008-01-08
mark@Lexington-19:~$ whereis azureus
azureus: /usr/bin/azureus /usr/share/man/man1/azureus.1.gz
mark@Lexington-19:~$ locate azureus
/opt/azureus
/opt/azureus/azureus
/opt/azureus/plugins
/opt/azureus/plugins/azupdater
/opt/azureus/plugins/azupdater/plugin.properties
/opt/azureus/plugins/azupdater/azureus.sig
/opt/azureus/plugins/azupdater/azupdaterpatcher_1.8.6.jar
/opt/azureus/plugins/azupdater/Updater.jar
/opt/azureus/plugins/azrating
/opt/azureus/plugins/azrating/azrating_1.3.1.jar
/opt/azureus/plugins/azupnpav
/opt/azureus/plugins/azupnpav/plugin.properties
/opt/azureus/plugins/azupnpav/azureus.sig
/opt/azureus/plugins/azupnpav/azupnpav_0.1.7.jar
/opt/azureus/plugins/azplugins
/opt/azureus/plugins/azplugins/azplugins_2.1.4.jar
/opt/azureus/README.txt
/opt/azureus/updateAzureus
/opt/azureus/Azureus.torrent.png
/opt/azureus/swt.jar
/opt/azureus/Azureus.png
/opt/azureus/installer.log
/opt/azureus/Azureus2.jar
/opt/azureus/TOS.txt
/opt/azureus/GPL.txt
/home/mark/.azureus
/home/mark/.azureus/tracker.config
/home/mark/.azureus/downloads.config.bak
/home/mark/.azureus/.certs
/home/mark/.azureus/net
/home/mark/.azureus/net/pm_7132.dat
/home/mark/.azureus/shares
/home/mark/.azureus/azureus.config
/home/mark/.azureus/.keystore
/home/mark/.azureus/tmp
/home/mark/.azureus/tracker.config.bak
/home/mark/.azureus/active
/home/mark/.azureus/active/F5000C8D29BF6B252DC2811E78E1697E80B7F754.dat
/home/mark/.azureus/active/F5000C8D29BF6B252DC2811E78E1697E80B7F754.dat.bak
/home/mark/.azureus/plugins
/home/mark/.azureus/plugins/azemp
/home/mark/.azureus/plugins/azemp/plugin.properties
/home/mark/.azureus/azureus.statistics.bak
/home/mark/.azureus/torrents
/home/mark/.azureus/downloads.config
/home/mark/.azureus/unsentdata.config
/home/mark/.azureus/azureus.config.bak
/home/mark/.azureus/dht
/home/mark/.azureus/dht/general.dat
/home/mark/.azureus/dht/addresses.dat
/home/mark/.azureus/dht/diverse.dat
/home/mark/.azureus/dht/contacts.dat
/home/mark/.azureus/ipfilter.cache
/home/mark/.azureus/.lock
/home/mark/.azureus/azureus.statistics
/home/mark/.azureus/logs
/home/mark/.azureus/logs/thread_1.log
/home/mark/.azureus/logs/v3.CMsgr_1.log
/home/mark/.azureus/logs/alerts_1.log
/home/mark/.azureus/logs/save
/home/mark/.azureus/logs/AutoSpeed_1.log
/home/mark/.azureus/logs/SpeedMan_1.log
/home/mark/.azureus/logs/debug_1.log
/home/mark/.azureus/logs/v3.PMsgr_1.log
/home/mark/.azureus/logs/seltrace_1.log
/usr/share/app-install/desktop/azureus.desktop
/usr/bin/azureus

---

### Post by Perfect Storm on 2008-01-08
Have you manually installed azureus at one time? It could explain two azureus.

---

### Post by zero-9376 on 2008-01-08
i believe automatix used to install azureus to /opt not sure if the packages in the repo do

---

### Post by Mark_in_Hollywood on 2008-01-08
> **Artificial Intelligence said:**
> Have you manually installed azureus at one time? It could explain two azureus.

If by manually, I think the Vuze was d/l from some website and then ./

it's sooo long ago, I've forgotten.

---

### Post by Perfect Storm on 2008-01-08
ok.
Here you go,

```
rm -rf ~/.azureus
cd /usr/bin
sudo rm -rf azureus
cd /usr/share/man/man1
sudo rm -rf azureus
cd /opt
sudo rm -rf azureus
cd /usr/share/app-install/desktop/
sudo rm -rf azureus.desktop
```


should do it.

NOTE: Make sure everything spell and perform correctly the rm command can be dangerous if done incorrectly.

---

