---
title: "I Trashed My Dapper"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by hobo on 2007-02-04
This AM when trying to get a wireless card to work (WMP54g Linksys) I trashed my Dapper image. It stops on config network during boot. This is a dual boot system.

1. Can I fix this without reloading Dapper?
2. If not, how do I reload Dapper to existing partitions (dapper). Without damaging the others.

I dont think I made any changes other than getting an update to what PCI cards it recognizes.

Real noob here.

---

### Post by kingmonkey on 2007-02-04
Are you sure it stops or ist it waiting?

It can wait for up to 1 min for a DHCP signal.

Try pressing Ctrl+C when it stops at that point.

You can probably repair this by reversing the things you did to "trash your dapper image" in recovery console.

In recovery console type dmesg - does it say anything about the problem there?

---

### Post by hobo on 2007-02-05
I can't get to the recover console. Ctrl-C does blast me out of the boot up stuff but it then goes to another screen and locks up.

---

### Post by dannyboy79 on 2007-02-05
try to boot to a live cd, then run fsck on the "unmounted" partition. sudo fsck /dev/hda2 (or whatever hard drive and partition it is) plus, you're gonna need to be way more specific as to what you did to "trash you dapper image". i mean, it's actually really hard to trash dapper. unless you were logged in as root which is really not smart at all! so tell us what you did and then we can maybe hel;p you.

---

### Post by hobo on 2007-02-06
The only thing I did, that I can remember, is to use ndiswrapper to load a driver for my wireless card. I did this under sudo I guess. Never as root.
I think I will remove the wireless card and see if it boots then. If so I will uninstall the driver and go from there. But that will later in the week. No time today.

---

### Post by AndyCooll on 2007-02-06
I vaguely remember have wireless card issues sometime back. Turned out that both my cable connection and wireless connection were competing with each other. 

So, are you trying to connect with both a normal cable connection and a wireless card connected? Are you able to temporarily disconnect your wireless card?

:cool:

---

### Post by hobo on 2007-02-06
Well, yes this is the case. I will disco the wireless and see what happens.

---

### Post by hobo on 2007-02-06
By removing the wireless card I was able to boot to the Ubuntu desktop. I will remove the driver for this WIFI card and try again. Thanks for the info. I really didn't want to reload.:biggrin:

---

### Post by hobo on 2007-02-06
I removed the NDISWrapper driver, reinstalled the wireless card and now it won't boot again. How can prevent the OS from doing anything with the wireless card until I get this resolved?

---

### Post by dannyboy79 on 2007-02-06
why do you keep leaving in your ethernet cord if you're trying to install a wireless card. unplug it and it should boot up. then you can configure your wireless. or you need to play with your /etc/network/interfaces file and comment out anything that relates to your ethernet interface which is normally eth0 and your wireless interface will either be ath0 or wlan0 (i think) i have the atheros chipset so mine is ath0.

---

### Post by aseneca on 2007-02-06
Check out some googles I did of your problem.

[http://www.ubuntuforums.org/archive/index.php/t-76577.html](http://www.ubuntuforums.org/archive/index.php/t-76577.html)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)


Good Luck 

AS

---

### Post by hobo on 2007-02-06
Well I edited the interface file and deleted all ref to RA0. Now I can boot with both cards in place. It looks like I need a linux driver RT61 and I have to compile it.......whoa. Not today, but I did find a howto in ref to this card on a site called NixCraft. Pretty intense for this noob.

[http://www.cyberciti.biz/tips/linux-install-and-configure-dlink-dwl-g-520-wireless-lan-pci-card.html](http://www.cyberciti.biz/tips/linux-install-and-configure-dlink-dwl-g-520-wireless-lan-pci-card.html)

thanks

---

