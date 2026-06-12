---
title: "Getting my built in wireless card working"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by dudeness3 on 2007-02-15
I just installed Ubuntu on my new laptop, and it has a built in wireless g card, but it wsill not turn on, I would like to know if this has happened to anyone else, and if you fixed it, how?

---

### Post by compiledkernel on 2007-02-15
Card type? 

or search through these and see what you get. 

[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by dudeness3 on 2007-02-15
I am not to sure, like I said, it's built in, I cannot take it out to check, all I know is that HP says it's "54g&#8482; 802.11b/g WLAN" that's all the info I have on it.

---

### Post by compiledkernel on 2007-02-15
Computer/laptop model?

---

### Post by dudeness3 on 2007-02-15
HP Compaq Presario V5000

---

### Post by lamalex on 2007-02-15
enable universe and restricted repos, in terminal do ```
apt-get install bcm43xx-fwcutter
```. answer yes and it should install the firmware for you. if for some reason it doesn't ask you if you'd like to extract the firmware, download [this file]("http://boredklink.googlepages.com/wl_apsta.o") and do ```
sudo bcm43xx-fwcutter -w /lib/firmware wl_apsta.o

bcm43xx-fwcutter -w /lib/firmware/`uname -r` wl_apsta.o
```

next do ```
sudo apt-get install network-manager-gnome
``` and reboot. should now work.

---

### Post by dudeness3 on 2007-02-15
I'm sorry, I am not very Linux savvy, please explain a little bit more, nothing you said is working.

---

### Post by tonyr1988 on 2007-02-15
Here ya go, slightly simplified:

1) Enable extra repositories: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29)

2) Open up a terminal: Applications -> Accessories -> Terminal

3) In the terminal, copy/paste:

> sudo apt-get install bcm43xx-fwcutter

(it will want your password - type your user password).

4) If it asks you to extract the firmware, choose Yes and skip to step 7. If it doesn't, do step 5:

5) Right-click and download [this]("http://http://boredklink.googlepages.com/wl_apsta.o") file to your Desktop.

6) Go back to the Terminal and type:

> cd ~/Desktop
sudo bcm43xx-fwcutter -w /lib/firmware wl_apsta.o
bcm43xx-fwcutter -w /lib/firmware/`uname -r` wl_apsta.o

7) In the Terminal, type:

> sudo apt-get install network-manager-gnome

(NOTE: Thanks to Iamalex for the instructions...I just n00bified them :D)

---

### Post by dudeness3 on 2007-02-15
I didn't understand at first, but then noticed it is for 6.10 Edgy, I will try it now. I will edit to tell you if it works.

EDIT: Yeah, I'm still having trouble, on step 3, I think I did everything correctly, but I get this:
```
steve@steve-laptop:~$ sudo apt-get install bcm43xx-fwcutter
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcm43xx-fwcutter
```

---

### Post by dudeness3 on 2007-02-18
Sorry for the double post(please don't state the obvious and tell me not to)
But I have a problem, I cannot add
```
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
```
Like it says to do, the other 4 I can add, just not those 2. Any suggestions?

---

### Post by dudeness3 on 2007-02-19
Anyone?
and now i'm getting this error
```
W: GPG error: http://medibuntu.sos-sts.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
```

---

