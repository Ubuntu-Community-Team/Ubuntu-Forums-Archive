---
title: "ath9k wireless headsup"
date: 2008-09-01
forum: Apple Hardware Users
---

### Post by {{corona}} on 2008-09-01
I used [instructions here]("http://ubuntuforums.org/showthread.php?t=874097&highlight=ath9k") to install the new ath9k and found some peculiar problems with it. I could reproduce keyboard and mouse freezes consistently- this is how
 
-> Suspend to ram worked the very first time. on wakeup Network Manager(and also wcid) both would connect to the network. everything worked perfectly
until
-> I suspend to ram the second time. On wakeup both Network Manager (and also wcid) would stall and eventually my trackpad and keyboard would turn unresponsive. would have to basically restart the computer.

While NM or wcid were trying to connect i would get these messages in my kernel.log

```

Sep  1 00:06:40 iamok-ubu kernel: [  323.541440] wlan0: associated
Sep  1 00:06:44 iamok-ubu kernel: [  327.494973] wlan0: deauthenticated
Sep  1 00:06:45 iamok-ubu kernel: [  328.490584] wlan0: authenticate with AP 00:1c:10:86:77:6f
Sep  1 00:06:45 iamok-ubu kernel: [  328.492241] wlan0: authenticated
Sep  1 00:06:45 iamok-ubu kernel: [  328.492244] wlan0: associate with AP 00:1c:10:86:77:6f
Sep  1 00:06:45 iamok-ubu kernel: [  328.494614] wlan0: RX ReassocResp from 00:1c:10:86:77:6f (capab=0x411 status=0 aid=1)
Sep  1 00:06:45 iamok-ubu kernel: [  328.494617] wlan0: associated
Sep  1 00:06:49 iamok-ubu kernel: [  332.462585] wlan0: deauthenticated
Sep  1 00:06:50 iamok-ubu kernel: [  333.458258] wlan0: authenticate with AP 00:1c:10:86:77:6f
Sep  1 00:06:50 iamok-ubu kernel: [  333.461558] wlan0: authenticated
Sep  1 00:06:50 iamok-ubu kernel: [  333.461561] wlan0: associate with AP 00:1c:10:86:77:6f
Sep  1 00:06:50 iamok-ubu kernel: [  333.463852] wlan0: RX ReassocResp from 00:1c:10:86:77:6f (capab=0x411 status=0 aid=1)
Sep  1 00:06:50 iamok-ubu kernel: [  333.463855] wlan0: associated
Sep  1 00:06:53 iamok-ubu kernel: [  337.418240] wlan0: deauthenticated
Sep  1 00:06:54 iamok-ubu kernel: [  338.413953] wlan0: authenticate with AP 00:1c:10:86:77:6f
Sep  1 00:06:54 iamok-ubu kernel: [  338.415607] wlan0: authenticated
Sep  1 00:06:54 iamok-ubu kernel: [  338.415610] wlan0: associate with AP 00:1c:10:86:77:6f
Sep  1 00:06:55 iamok-ubu kernel: [  338.417959] wlan0: RX ReassocResp from 00:1c:10:86:77:6f (capab=0x411 status=0 aid=1)
Sep  1 00:06:55 iamok-ubu kernel: [  338.417961] wlan0: associated
Sep  1 00:06:58 iamok-ubu kernel: [  342.379875] wlan0: deauthenticated
```

The only solution i have as of now is to avoid using the ath9k and revert back to madwifi [driver here]("https://help.ubuntu.com/community/MacBookPro#Wireless")

Hope this is of help.

---

### Post by SmileCat on 2009-01-25
I have the exact same issue here on openSUSE.

First suspend/resume cycle works without any problems.
On the second resume networkmanager doesn't connect and my keyboard locks up.

This doesn't happen with madwifi.

Is there any solution yet?

--

Lenovo T60
openSUSE 11.1
Kernel 2.6.27.7-9-pae
Atheros AR5418/5008 Wireless Network Adapter
Radeon Mobility X1400 with radeon driver

---

### Post by mcgrof on 2009-01-27
Please read:

[http://wireless.kernel.org/en/users/Drivers/ath9k#Getthelatestath9kdriver](http://wireless.kernel.org/en/users/Drivers/ath9k#Getthelatestath9kdriver)

---

### Post by SmileCat on 2009-02-19
Thank you very much!

The latest ath9k driver from compat-wireless is just great. Better connectivity, no hangs, increased transmission rates AND the led finally works!

If you are on openSUSE and don't want to compile the drivers by yourself (which is really easy), you can go to [http://software.opensuse.org/search]("http://software.opensuse.org/search")
and search for compat-wireless, which will give you some rpms to install.

Bye, SmileCat

---

### Post by BBUCommander on 2011-02-20
I can confirm that this solves the problems with the Atheros AR9285 card in Toshiba NB305. Using the latest bleeding-edge nightly build of compat-wireless from wireless.kernel.org solved all that ailed the Atheros card in my Toshiba NB305.  Wireless N works quite well now and I am getting the same speedtest results as my ethernet connected PC.  BTW, I am running Xubuntu 11.04 (Natty) Alpha 2, which also takes care of a myriad of other problems my NB305 was giving me.

---

