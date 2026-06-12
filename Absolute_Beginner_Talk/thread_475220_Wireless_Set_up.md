---
title: "Wireless Set up"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Haruko147 on 2007-06-15
Hi, I'm 100% new to linux, and just installed to my laptop about 30 minutes ago.

What I have so far is the connection manager up, and under wireless connection I have clicked the properties tab and typed in my ssid, wep key, and all that good stuff. This has changed the icon in the top right from monitors with the red x, to just plain monitors which I guess means that my computer is in connection with the router if its like windows.

However, my firefox still doesn't connect to the internet which is my test for if it is actually functioning. I've tried going through the troubleshotting and managed to "sudo lshw". I see a bunch of stuff under the heading pcmcia, "sudo pccardctl ident" gives me socket 0: and nothing else. Aparently I'm suppose to add something to the file, but it loses me, if that is indeed the solution.

Also in case it matter, I do have my second windows laptop hooked up to the router, a westell versalink, so it does work I needed to port forward a program on my windows laptop, so I have static ips set up, but none of that should matter really I think.

Let me know if theres anymore information you need, and thanks in advance for the help! hopefully I can get my linux up and running tonight!

---

### Post by Bachstelze on 2007-06-15
Okay, last one for tonight :p

What kind of wireless card do you have ?

---

### Post by Haruko147 on 2007-06-15
I'm not exactly sure how to check that, but under the pcmcia (with lshw) I see it says PCI4510 PC card Cardbus controller from texas instruments with driver=yenta_cardbus

---

### Post by Bachstelze on 2007-06-15
So you have a PCMCIA card ? Try

```
lspci
```

Also, to check whether your wireless is properly detected, you can try

```
sudo iwconfig
```

---

### Post by Haruko147 on 2007-06-15
I wish I could copy and paste from my other computer lol

lspci gives me a big list of 15 things, under ethernet controller: Broadcom corporation NetXtreme BCM5705M Gigabit Ethernet

under Cardbus bridge, the one I mentioned above

under Network controller: Broadcom Corp. BCM4309 802.11a/b/g

iwconfig says no wireless extensions for lo or eth0, but eth1 gives me a bunch of stuff. Invalid in some of the categories, and no essid mentioned but it has the nickanme "Broadcom 4306

---

### Post by Bachstelze on 2007-06-15
Okey dokey, try this :

```
sudo iwconfig eth1 essid YOUR_ESSID key YOUR_WEP_KEY
sudo dhclient eth1
```

If you see something like :

```
DHCPACK from 10.1.204.1
bound to 10.1.204.114 -- renewal in 36000 seconds.

```

that means you're connected and you can browse the Interweb :)

---

### Post by Haruko147 on 2007-06-15
ök, so I typed that in and nothing happened after the first line
with dhclient eth1 it gave me:

SIOCSIFFLAGS: No such file or directory
Listening on:  LPH and other stuff
Sending on: LPH and same stuff
Sending on: socket/fallback
recieve_packet failed on eth1: Network is down

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down

No DHCPOFFERS received
No working leases in persistent database - sleeping

---

### Post by Bachstelze on 2007-06-15
Try

```
sudo ifconfig eth1 up
```

before the two others.

---

### Post by Haruko147 on 2007-06-15
SIOCSIFFLAGS: aucun fichier ou répertoire de ce type

in case you don't actually speak french no file or directory of that type

---

### Post by Bachstelze on 2007-06-15
*Smacks forehead*

You have a Broadcom card, which Ubuntu is currently using the bcm43xx driver for. However, that driver doesn't work until you get a firmware for your card. For legal reasons, the firmware cannot be shipped with Ubuntu. Can you get your laptop wired temporarily ?

---

### Post by Haruko147 on 2007-06-15
I do have wireless on this laptop I'm using now, and an external hardrive that I can use to move files in between the computers. I just checked that the hardrive does in fact work with linux. ^^

---

### Post by Haruko147 on 2007-06-15
I just found this

[http://ubuntuforums.org/showthread.php?t=185650](http://ubuntuforums.org/showthread.php?t=185650)

so as soon as I figure out exactly what they are saying to do it might fix this? Im posting before I actually have read it fully

---

### Post by Bachstelze on 2007-06-15
Yes, if you do what is told there, it should work :)

---

### Post by Haruko147 on 2007-06-15
awesome, thanks for the help! *gets to work on shuffling files around*

---

