---
title: "No Azureus in Synaptic?"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by olieviya on 2005-12-18
I type in "Azureus" to search and it doesn't find anything, what is wrong?

I've followed all the steps to getting the new repositories and I seem to have them since most other programs  show up, is Azureus not in Synaptic?

---

### Post by Deaf_Head on 2005-12-18
I'm new, so I could be wrong but I think I have all the repositories set up properly and it doesn't show up in my search either.

[https://wiki.ubuntu.com/AzureusHowTo?highlight=%28azureus%29](https://wiki.ubuntu.com/AzureusHowTo?highlight=%28azureus%29)

Those are instructions on how to install it though, pretty simple stuffs

---

### Post by olieviya on 2005-12-18
Ta

---

### Post by Perfect Storm on 2005-12-18
The non-.deb way but you get the newest version out there if there come a newer release:

(remember to have java installed)
Download Azureus here: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) choose Linux version 2.3.0.6

```

cd /where/you/saved/the/file
sudo tar jxvf Azureus_2.3.0.6_linux.tar.bz2 -C /opt/
sudo chown -R root:root /opt/azureus/
smeg

```

Make the launcher under **Internet**
**Name:** Azureus
**Command:**  /opt/azureus/azureus
**Icon:** /opt/azureus/Azureus.png


Enjoy ^^


.:=The AI Dude=:.

---

