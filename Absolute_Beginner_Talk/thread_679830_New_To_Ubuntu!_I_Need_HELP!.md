---
title: "New To Ubuntu! I Need HELP!"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by avafreak182 on 2008-01-27
Well, I just installed Ubuntu.

I need to know where I can get drivers. And updates.

Most importantly, I have a Netgear wireless G PCI adapter, how can I make it work?

Thanks!

---

### Post by Jelmoh on 2008-01-27
Updates are handled automatically (You see it in the top of your screen, quite obvious so don't worry about that!)
Drivers, you don't really need drivers, sound drivers are handled by Ubuntu (ALSA most of the time, is also the best) And video drivers depend on your graphics card! :)
I heard Envy is a good way to acquire the latest drivers, you can download Envy from the repositories (System -> Administration -> Synaptic)

And your wireless network adapter, sorry, I don't know a thing about that.. :$
So for that you'll just have to wait for somebody else to answer! ;)

Great that you chose Ubuntu! :)
Good Luck! ;)

---

### Post by avafreak182 on 2008-01-27
Ahh. Anyone help with wireless?

---

### Post by avafreak182 on 2008-01-27
No one :(?

---

### Post by mister_pink on 2008-01-27
Try System, Admin., Restricted drivers manager. I dont have wireless, but I think some wireless cards need closed source drivers which I think you can install from there.

---

### Post by avafreak182 on 2008-01-27
> **mister_pink said:**
> Try System, Admin., Restricted drivers manager. I dont have wireless, but I think some wireless cards need closed source drivers which I think you can install from there.

All that is there is my video card. UGHGHHH

---

### Post by jan quark on 2008-01-27
please post the results of the following terminal commands

iwconfig
ifconfig
sudo iwlist scan
lspci

they will dispaly additional information about your network status

---

### Post by erginemr on 2008-01-27
Maybe I am not the one to answer this question, since I am not using any wireless modem either, but AFAIK, there is a tool "ndisgtk", which can be installed via:
```
sudo aptitude install ndisgtk
```
which will install "ndiswrapper" tools alongside, the technology which allows wireless modem owners to use their windows (*.inf) drivers from under Linux. The following site discusses this issue in depth:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by ugm6hr on 2008-01-27
We need a bit more detail about the **exact** Netgear PCI card you have.

Post the output from:
```
lspci
lshw -C network
```

And tell us the exact model number (if you know it).

Also:
1. What encryption do you use on your router?
2. Do you use DHCP or fixed IP on your router?

And do you have an ethernet connection available at the moment - if not - how are you online?

---

### Post by avafreak182 on 2008-01-27
How do I run "terminal commands"?

---

### Post by Abu_Dayya on 2008-01-27
To ryn terminal commands just click ALT + F2, or you can find it in Apps -> Accesories -> Terminal

And for the wireless drivers follow this guide: [https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html)

The .inf files should be on the CD you got with the adapter. Or you can install the driver from NETGEAR website and find the .inf file from what you've downloaded

Hope this helps

---

### Post by jan quark on 2008-01-27
just open the terminal and type it into it

---

### Post by ugm6hr on 2008-01-27
> **avafreak182 said:**
> How do I run "terminal commands"?

See the link in my signature below - Enter Code....

---

### Post by avafreak182 on 2008-01-27
Well. No one has helped so far. At all. The Windows driver for the adapter is a .exe file. How can I run it? This is reallllllly making my mad.

Also, when I type in commands, a window flashes, and goes away, so thats a big not gonna happen.

---

### Post by avafreak182 on 2008-01-27
Also: my wireless card is: Netgear WG311v3

---

### Post by ugm6hr on 2008-01-27
> **avafreak182 said:**
> Well. No one has helped so far. At all. The Windows driver for the adapter is a .exe file. How can I run it? This is reallllllly making my mad.

Also, when I type in commands, a window flashes, and goes away, so thats a big not gonna happen.

You probably can't run the exe in Ubuntu.  You *may* be able to extract the drivers from it.

Which version of Ubuntu are you using?  There is clearly a problem with your installation if you cannot get the Terminal to work.

And you still haven't supplied some of the info regarding your network I asked for.

EDIT:

A quick google suggests you need ndiswrapper for wifi:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)
See numbers 29 & 35.  

Have you got files WG311v3.INF and WG311v3XP.sys on the CD somewhere?
Although it may be better to use files confirmed to work: [http://www.jimbo7.com/wiki/files/good_WG311v3-driver.tgz](http://www.jimbo7.com/wiki/files/good_WG311v3-driver.tgz)
Ref: [http://www.jimbo7.com/wiki/index.php?title=WG311v3](http://www.jimbo7.com/wiki/index.php?title=WG311v3)

This is what you need to get on your way with ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

---

