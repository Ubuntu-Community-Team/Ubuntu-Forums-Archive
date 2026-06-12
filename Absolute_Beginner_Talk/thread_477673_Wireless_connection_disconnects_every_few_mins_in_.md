---
title: "Wireless connection disconnects every few mins in fiesty"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by i.nihilist on 2007-06-18
Hi.
Does anybody has the same problem like me.
I have a Intel Pro wireless 3495 wireless card in my lappy and it works fine both in windows and Fedora.
But in Fiesty frawn..I inoticed that it disconnects every few mins and then reconnects again?

any suggestions?

---

### Post by paradoc on 2007-06-18
I had the same problem, but in reverse from yours, winXP was erratic, but Feisty is fine.
I have a laplink router and Feisty recognises this, and connects with the wiggly thingy almost immediately,whereas I have to juggle with XP.
Are you possibly at the furthest reach of your signal?..this leads to instability;)

---

### Post by panso on 2007-07-27
hi i.nihilist

Its the same for me in ubuntu. I have a wireless card in my laptop that worked fine in 6.x ubuntu but with feisty it disconnects every few mins.

Did you have any luck hunting down a fix?

---

### Post by buntunub on 2007-07-28
Same issue here. Broadcom 4311/Dell 1390 card. Disconnects erraticly with no error messages so no clue as to whats going on

---

### Post by sureinlux on 2007-08-03
Hi All,
 My wireless device is and I also have my wireless disconnects.

```
Broadcom Corporation BCM4310 UART (rev 01)
```

I have a workaround for this. I always have my SquirrelMail which refreshes the page every 30 sec

---

### Post by ugm6hr on 2007-08-03
> **i.nihilist said:**
> Hi.
Does anybody has the same problem like me.
I have a Intel Pro wireless 3495 wireless card in my lappy and it works fine both in windows and Fedora.
But in Fiesty frawn..I inoticed that it disconnects every few mins and then reconnects again?

any suggestions?

This is a known bug with Network Manager and WPA.  If you are using WPA - try Wicd instead - see my signature.

---

### Post by walkerk on 2007-08-03
> **ugm6hr said:**
> This is a known bug with Network Manager and WPA.  If you are using WPA - try Wicd instead - see my signature.

+1 for Wicd. I had the same issues with my Broadcom and i ditched network-manager for wicd.. everything works flawlessly..


[Wicd]("http://wicd.sourceforge.net")

Do the following:
```
echo 'deb http://wicd.longren.org feisty extras' | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get -d install wicd network-manager network-manager-gnome
```

The -d option downloads the package without installing. (find it in /var/cache/apt/archives .. ensure that it is there before continuing)
You downloaded Network Manager as well so that you can fall back on it if WICD doesn't suit your needs. This might tell you that you have the newest version..

Now remove network-manager. (You have to remove this because it conflicts with WICD)
```
sudo apt-get remove network-manager network-manager-gnome
```

Now move to /var/cache/apt/archives:
```
cd /var/cache/apt/archives
```

Verify the file name: (I believe its wicd_1.3.1_all.deb)
```
ls | grep wicd
```

Install the package:
```
sudo dpkg -i wicd_1.3.1_all.deb
```

---

