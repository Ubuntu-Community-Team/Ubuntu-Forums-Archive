---
title: "Lost Network access and knetworkmanager not installed"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by bmachia on 2008-03-15
Ok, messed up big; this time.

System: IBM Thinkpad A31, Kubuntu Gutsy 7.1, with KDE3 desktop.
Network: Linksys WRT54G

I was reading posts last night, and realized how open I was using ndiswrapper and knetworkmanager to access the web without WAP or WPA2.  I had perfect communication, but it was completely open to the neighborhood. 

So, I went into Synaptic Package manager and install WPAsuppliant and then setup my Router for Wireless security WPA2, Personal.  That’s when things started to get strange and I eventually lost all LAN access from my laptop.  Both eth0 (wired) and eth1 (wireless)

My initial thoughts were that WPA was not configured property and after reading, and reading and reading I installed ‘kwlan’ to help configure.  ‘kwlan’ slowed my machine to a crawl, and I could barely access anything or get a response from a click and still no communication or connections (anywhere).

I have since uninstalled kwlan, WPASuppliant and returned my Wireless router to open and clear communication.

But, somewhere in the installation or configuration process “knetworkmanager” was uninstalled. When I try;
sudo apt-get install network-manager-kde or
sudo apt-get install knetworkmanager

It starts to process the install and then errors with; ‘Failed to Fetch’.

I guess that makes since. I no longer can communicate with anything.  How could I expect it to fetch software.

Can anyone get me some advice, what I should check for and uninstall or how I could install software without a network connection.

My eventual goal with be to have some type of wireless security.

Hoping to hear from someone.

Bill

---

### Post by handydan918 on 2008-03-15
> I guess that makes since. I no longer can communicate with anything. How could I expect it to fetch software.

Can anyone get me some advice, what I should check for and uninstall or how I could install software without a network connection.

Plug the ethernet cable in and do ```
sudo dhclient
```

Only other possibility is to download the desired packages and "sneakernet" them onto the machine in question...

---

### Post by bmachia on 2008-03-15
handydan918  --> Thank You - Thank You - Thank You

Thanks the 'sudo dhclinet' worked!  I have been able to install knetworkmanager.

Can you offer any readings on the correct way to install and configure WPA2 from this point?  

Bill

---

### Post by handydan918 on 2008-03-18
> **bmachia said:**
> handydan918  --> Thank You - Thank You - Thank You

Thanks the 'sudo dhclinet' worked!  I have been able to install knetworkmanager.

Can you offer any readings on the correct way to install and configure WPA2 from this point?  

Bill

Meh, sorry. I only use mac filtering at home and I just don't send sensitive stuff by radio broadcast...

---

