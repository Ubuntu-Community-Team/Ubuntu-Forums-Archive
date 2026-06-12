---
title: "Is it possible to update manually?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-14
Is it possible for me to download update packages for Dapper manually in win xp? i.e. through packages.ubuntu.com and then boot into Dapper and install them?

If yes, what do I search for?

---

### Post by aysiu on 2006-11-14
It's possible, but extremely inconvenient, as you would have to track down all the dependencies. Also, how do you know when packages have updated?

If you have a .deb file, just double-click it to launch *gdebi*, which will install it for you. 

If you prefer the terminal: ```
sudo dpkg -i *nameoffile*.deb
```

---

### Post by scrooge_74 on 2006-11-14
> **PartisanEntity said:**
> Is it possible for me to download update packages for Dapper manually in win xp? i.e. through packages.ubuntu.com and then boot into Dapper and install them?

If yes, what do I search for?

But why don't you do it directly from Ubuntu, just do sudo apt-get update and then sudo apt-get upgrade

---

### Post by aysiu on 2006-11-14
> **scrooge_74 said:**
> But why don't you do it directly from Ubuntu, just do sudo apt-get update and then sudo apt-get upgrade
It sounds as if internet may not be working on Ubuntu for PartisanEntity.

---

### Post by PartisanEntity on 2006-11-14
I am still working on getting my wifi card to work in Dapper. I don't have access to ethernet at the moment. This is why I was wondering if I could download updates manually, but if I have to track down all the dependencies that would be a nightmare...

---

### Post by Frak on 2006-11-14
Oh I'd that problem, get the NDIS file and install ndiswrapper off the Ubuntu disk (go to synaptics->add cd) go to terminal and type...

```
sudo ndiswrapper -d 
```

And then drag the file into the terminal and push enter, right click the panel and click add to panel->network monitor, click on network monitor to open it, depending on your card, mine was wlan0 becuase it was a Linksys, depending on yours it may be different,...

If I missed anything just reply.

---

### Post by PartisanEntity on 2006-11-15
> **Frak said:**
> Oh I'd that problem, get the NDIS file and install ndiswrapper off the Ubuntu disk (go to synaptics->add cd) go to terminal and type...

```
sudo ndiswrapper -d 
```

And then drag the file into the terminal and push enter, right click the panel and click add to panel->network monitor, click on network monitor to open it, depending on your card, mine was wlan0 becuase it was a Linksys, depending on yours it may be different,...

If I missed anything just reply.

Thanks for the advice, are ndiswrapper and network monitor on the Dapper installation CD?

---

### Post by aysiu on 2006-11-15
*ndiswrapper* is on the installation CD.

---

### Post by PartisanEntity on 2006-11-15
Well, I went out and bought an ethernet cable, reinstalled and picked one tutorial and followed it, I am now proudly posting through my wireless home network with wpa encryption :)

Thank you for the help to all :)

---

