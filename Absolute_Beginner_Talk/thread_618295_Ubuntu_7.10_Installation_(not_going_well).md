---
title: "Ubuntu 7.10 Installation (not going well)"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Buk on 2007-11-20
I thought I would install Ubuntu 7.10 on this old Gatewat computer I have.  The computer has ans AMD K7 processor, Radeon 9200 SE graphics card and a RTL8139 Ethernet card from D-Link Systems.  

_Graphics_
Ubuntu selected a generic graphics driver and profile for my monitor.  The graphics are operating as if I had a flat panel display.  I don't.  If I try to change the settings, I loose all video (I get a black screen).  I've tried several different video selections.  I haven't found anything that works.  My monitor is an Hitachi SuperScan Pro 600.  That's not even listed.  I've tried a few different monitor choices but haven't found anything that helps there either.

_Ethernet_
I've used a phyical cable and plugged directly into my router (Liknksys Wireless-G Broadband Router).  I have lights both on the router and eithernet card indicating a connection/communication.  Ubuntu doesn't seem to recognize a connection.  I've checked the list of devices in Ubuntu and it tells me there's a RTL8139 Ethernet card.  But I have no internet.  I used the Terminal as outlined in the help section to issue commands to ping, configure and whatever else.  The terminal continues to tell me there is no device.

I've downloaded Linux drivers for both of these but don't know how to install them.  I'm not even sure about the drivers as the web sites said I must have something else installed (don't remember, some type of Linux software) before the drivers could be installed.  I took my best guess.

So, I have no internet and the graphics card is running in some crazy graphics mode.  Anyone got any ideas?

Thanks

---

### Post by Dr Small on 2007-11-20
You may wish to try the following command to reconfigure your xserver:
```
sudo dpkg-reconfigure xserver-xorg
```

And for ethernet, have you gone into System > Administration > Network and selected eth0 as your ethernet device ?

Dr Small

---

### Post by Buk on 2007-11-20
> **Dr Small said:**
> You may wish to try the following command to reconfigure your xserver:
```
sudo dpkg-reconfigure xserver-xorg
```

And for ethernet, have you gone into System > Administration > Network and selected eth0 as your ethernet device ?

Dr Small
When I tried the sudo dpkg-reconfigure xorg-xserver,  I got "Package xorg-xserver is not installed and no info is available".  (I'm assuming I typed it all in correctly)

As far as going to System>Administration>Network and selecting eth0 as the device.  No where on any tab of that screen do the words "eth0" appear.  The dropdown located at the top is blank and there are no selections available.  I have a check next to "Wired Connection" and have that set to "Automatic configuration (DHCP)"
The General tab shows my host name and domain name.  The DNS tab has nothing in the DNS Servers and Search Domains.  The Hosts tab displays the following (I have no idea what any of this means):
127.0.0.1 localhost
127.0.1.1 ubuntu-computer.WORKGROUP
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff03::3 ip6-allhosts

Buk

---

### Post by Dr Small on 2007-11-20
I apologize, I had it wrong the first time (backwards that is), and noticed taurus had posted it elsewhere, and corrected mine. You may now try the revised command, from above.

Dr Small

---

### Post by Buk on 2007-11-20
> **Dr Small said:**
> I apologize, I had it wrong the first time (backwards that is), and noticed taurus had posted it elsewhere, and corrected mine. You may now try the revised command, from above.

Dr Small


Ok. Triedsudo dpkg-reconfigure xserver-xorg.  Rebooted the computer and now as Ubuntu loads the screen will go black (monitor goes into standby) and everything comes to a complete stop.  The only difference I see using the methon you suggested and going through Administration is at least setting a graphics drive through Adminisrtation I could recover.  Now the configuration file has been overwritten.  Do I have to completely re-install Ubuntu or is there some way to get back the old config file?

Info...
Ubuntu DID correctly identify the graphics card in the computer as an ATI Radeon 9200 SE (which I selected).  It could not identify the monitor so I gave it some parameters to work with (refresh rates, etc...).  Don't know if it means anything, but as I was progressing through the reconfiguration, the Terminal screen would flash up for a short period.  When I was all done and returned to the Terminal, this is what it said:
paul@ubuntu-computer:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for paul:
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071120094422
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
paul@ubuntu-computer:~$ 

Don't know what all the fatal errors are about.

So what should I try to get restored and or get a good graphics driver installed?

Buk

---

