---
title: "OS X Networking Problem"
date: 2007-07-20
forum: Apple Intel Users
---

### Post by anujseth on 2007-07-20
I know this is a OS X related issue but I have more faith in Ubuntu users and hence am posting it here rather than a Mac Forum first.

The problem is pretty simple I guess maybe I just overlooked something,

I have 4 laptops(including this one MacBook) at home  and a Desktop PC. 2 Laptops  Win XP, 1 Ubuntu, my MacBook runs Ubuntu and OS X. the 4 laptops are connected by 802.11 G wireless cards to a 3Com Router which is intern bridged with a DSL modem to provide all hosts Internet. The PC is connected by LAN cable. All hosts have the Internet running smoothly no problems with that. The problem is really strange and moreover only confined to OS X and that to only when using Airport that is the wireless card. The Internet works fine, I cannot however ping or for that matter share things with the other windows hosts or the Ubuntu machine. If however i put in a Lan cable into the Gigabit Ethernet port I can ping everyone receive pings etc and share resources. 

This is not a firewall issue I have done all that and actually test with all firewalls down first before adding exceptions to tables etc. The Airport Connection cannot see any other host on the LAN apart from the router. arp -a confirms this and when using Airport the kernel routing tables show no knowledge of other hosts. arp -a when using the Gigabit port however gives detailed machine names routes etc. so its really a thing with airport. To make things even stranger I can host services from my MacBook using the Airport card because like I said it sees the router and the Internet works I have tested Tomcat Apache services VNC etc all work from the Internet. 

If I boot ubuntu into Ubuntu I can do everything with the Wireless and the problem vanishes. I first thought it was one of those Airport not working with certain routers thingies but even after all of apples updates ... nothing.

any suggestions.

---

### Post by cyberdork33 on 2007-07-20
I have actually run into similar problems, but never really found the root source. I think it may be the router though.

---

### Post by anujseth on 2007-07-20
If its the router then its an OS X related issue ... cause windows and ubuntu and infact ubuntu using the mad wifi drivers snapshots on the same macbook has no such problem ... 

i ve really looked and looked ... found nothing ...  nothing at all

---

### Post by citadelgrad on 2007-07-21
Have you tried deleting the Network preferences file? /Library/Preferences/SystemConfiguration/preferences.plist

You may have a persistent static route only configured on your Airport Card? 
Try: 'route flush'

Try a static ARP entry:
arp -s hostname macaddress

Good Luck!

---

### Post by anujseth on 2007-07-21
nope ... nothing

---

### Post by citadelgrad on 2007-07-21
Verify permissions with Disk Utility?

Crap, i don't know. Dare I say, repair the OS install. You definitely have some weird software issue going on.

---

### Post by anujseth on 2007-07-21
ha! no thats not it ... permissions are a nonner ... done multiple os installs already it always comes back

---

### Post by citadelgrad on 2007-07-21
I would recommend browsing through the information you can get through the defaults command. There is probably a configuration file that persists even when you repair the OS. Maybe /Library/Preferences/.GlobalPreferences 

#Gives a list of all the default settings.

defaults domains | defaults read

That's pretty much all I have at this point. I'm not a Mac expert and my wife is using the only Mac in the house.

Let me know if you figure it out.

---

### Post by anujseth on 2007-07-21
nice ... this pumps out a lot of information ... will definitely post back if i find the cause

---

### Post by anujseth on 2007-07-21
```
anuj-seths-computer:~ admin$ arp -s 192.168.1.4 00:14:6c:71:52 temp
arp: writing to routing socket: Operation not permitted

```

this is what i keep getting ... and the arp tables are below since i did nt want to bug my dad at 2 in the night i just ping his machine his firewall is on but the arp table when using the gigabit ethernet registers it promptly

3Com Router - 192.168.1.1
Airport - 192.168.1.2
 
```
arp -a 
? (192.168.1.1) at 0:f:cb:fa:36:32 on en1 [ethernet]

```

```
anuj-seths-computer:~ anujseth$ arp -a
? (192.168.1.1) at 0:f:cb:fa:36:32 on en1 [ethernet]
anuj-seths-computer:~ anujseth$ ping 192.168.1.4
PING 192.168.1.4 (192.168.1.4): 56 data bytes
^C
--- 192.168.1.4 ping statistics ---
2 packets transmitted, 0 packets received, 100% packet loss
anuj-seths-computer:~ anujseth$ arp -a
? (192.168.1.1) at 0:f:cb:fa:36:32 on en1 [ethernet]
? (192.168.1.4) at (incomplete) on en1 [ethernet]
anuj-seths-computer:~ anujseth$ 
```

Gigabit Ethernet - 192.168.1.5

```
arp -a          
? (192.168.1.1) at 0:f:cb:fa:36:32 on en0 [ethernet]
? (192.168.1.4) at 0:14:6c:71:52:bd on en0 [ethernet]
```

---

### Post by anujseth on 2007-07-21
[http://www.mac-forums.com/forums/showthread.php?t=70333](http://www.mac-forums.com/forums/showthread.php?t=70333)

---

### Post by anujseth on 2007-07-27
a cousin of mine is here to stay and behold i can ping her macbook!!

---

