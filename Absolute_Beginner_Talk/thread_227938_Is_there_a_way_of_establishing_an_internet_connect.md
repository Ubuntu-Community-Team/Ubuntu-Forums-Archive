---
title: "Is there a way of establishing an internet connection via the terminal?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by Kulgan on 2006-08-02
The normal Network settings app is freaking out, it seems that for some reason it does not like me. No errors messages, just no internet connction. It finds the wireless card well enough, but that is about where it stops. 

Therefore, I was wondering of there is any way at all of getting the terminal to do it. From what I understand of linux is that everything you do has a meaning in "terminal language", but I have no idea how to do it myself. 

Thanks,
K

---

### Post by tkjacobsen on 2006-08-02
Configure your card in the network interfaces file:
```
sudo nano /etc/network/interfaces
```

then add the following lines:
iface wlan0 inet dhcp

(this is if wlan0 is your wireless device. You can check that using the "lspci"-command in the terminal) This will configure your wireless to fetch an dhcp address

then:
```
sudo ifup wlan0
```

---

### Post by Kulgan on 2006-08-02
That is already in there. My wireless card is eth1 as far as the graphical network settings is concerned. I noted that the only one of the entries in the file that did not have "auto <name>" was eth1, so I added that. After reboot, no news. Shouldn't I have to enter the WEP key somewhere or other?

---

### Post by tkjacobsen on 2006-08-02
My entry for the wireless device looks like this:
(note i have static ip configuration. If using dhcp ignore address, netmask and gateway...)
                                                                            iface ra0 inet static
address 192.168.1.22
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid antarctis
wireless-key s:*************

13x* represents my wep key

---

### Post by Kulgan on 2006-08-02
so the "eth1" section for mine shoudl look something like 

iface eth1 inet dhcp
wireless-essid home
wireless-key s:*************

? I'll give that a try, thanks.

do I have to reboot between each edit? Would you expect DNS to have anything to do with this?

---

### Post by alan yeates on 2006-08-02
> **tkjacobsen said:**
> My entry for the wireless device looks like this:
(note i have static ip configuration. If using dhcp ignore address, netmask and gateway...)
                                                                            iface ra0 inet static
address 192.168.1.22
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid antarctis
wireless-key s:*************

13x* represents my wep key
This is just my problem too! I have done everything you say, and my wireless card is active, but still no internet!

---

### Post by Kulgan on 2006-08-02
What does the 's:' in front of the wep do? is there meant to be a colon in front of the essid, aswell? Not to sound too critical, but this isn't really making any sense. Thanks for helping, however! 

@alan yeates:
I had something odd about that on the first machine. Instead of closing with the "OK" button, try just closing the window. This is different, I think. Does it take a long time for the "Activating interface" to close itself?

---

### Post by stormblue on 2006-08-02
Replace eth2 with whatever your wireless card is

Try this:

```
sudo iwconfig eth2 up
```

This brings up your wireless card.  It should flash or at least light up, if it hasn't already

```
sudo iwconfig eth2 essid network_name
```

configures the network name
```

sudo iwconfig eth2 key xxxxxx
```

configures the network key.  You may try ```
sudo iwconfig eth2 key open xxxxx
``` instead

```

sudo dhclient eth2
```

DHCP client request.

If none of this works try doing a ```
iwconfig eth2
``` and paste the output

---

### Post by tkjacobsen on 2006-08-02
From iwconfig manual:
You can also enter the key as an ASCII  string  by  using  the  s:  prefix.

for additional information if you're using another kind of key:```
man iwconfig
```

---

### Post by alan yeates on 2006-08-02
> **Kulgan said:**
> What does the 's:' in front of the wep do? is there meant to be a colon in front of the essid, aswell? Not to sound too critical, but this isn't really making any sense. Thanks for helping, however! 

@alan yeates:
I had something odd about that on the first machine. Instead of closing with the "OK" button, try just closing the window. This is different, I think. Does it take a long time for the "Activating interface" to close itself?
yes, although I have a pretty quick machine, I have to wait ages to close it, it looks as if it is going to hang, but eventually dissapears!

---

### Post by alan yeates on 2006-08-02
I would guess that the s: thing is to denote a 'string' rather than the hexadecimal key?

---

### Post by Kulgan on 2006-08-02
Didn't get any error messages exept iwconfig eth1 up 
(Error : unrecognised wireless request "up") 
and dhclient (where it said "SIOCSIFFLAGS: No such file or directory exists" followed by that the network was down when it tried to send packets.

> **stormblue said:**
> 
If none of this works try doing a ```
iwconfig eth2
``` and paste the output

```

user@computer:~# iwconfig eth1
eth1  IEEE 802.11b/g ESSID:"home" Nickname:"Broadcom 4306"
      Mode:Managed Access Point: Invalid<?!?>  Bit rate=1 Mb/s
      RTS thr:off Fragment thr:off
      Encryption Key:****-****-****-****-****-** <yes, I enter it in hex every single time...> Security mode:open <?>
      Link Quality:0 Signal level:0 Noise level:0
      Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
      Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```


> yes, although I have a pretty quick machine, I have to wait ages to close it, it looks as if it is going to hang, but eventually dissapears!
then we have something similar - or are just equally stupid :D

---

### Post by stormblue on 2006-08-02
do sudo ifconfig eth2 up


Sorry, I put a "f" instead of a "w" in there.  But it should be working anyway now.

---

### Post by Kulgan on 2006-08-02
that gives "SIOSCIFFLAGS: No such file or directory"...

---

### Post by stormblue on 2006-08-02
> **Kulgan said:**
> that gives "SIOSCIFFLAGS: No such file or directory"...

that's the output of 

```
sudo iwconfig eth1 up
```

right?

---

### Post by Kulgan on 2006-08-02
no, it was the output of "sudo ifconfig eth1 up". the output of "sudo iwconfig eth1 up" is "Error : Unrecognised wireless request "up"".

Anyways, going to bed now - so don't expect answers for the next few hours :p

---

### Post by stormblue on 2006-08-02
Okay, sorry.  I always get ifconfig and iwconfig messed up.  Anyway, you wouldn't happen to have broadcom chipset?  I've read online about driver issues with the chip that generates the error.  Unfornately, I'm unable to help at this point as I've never used one.  But that might get you moving in the right direction.

---

### Post by Kulgan on 2006-08-03
so what you're saying is that it identifies the card, but not the chipset on it? That's wierd, cause it appears to be working fine with the ethernet card... I would hate to have to lay a cable all the way, and due to the fact that I'm not even sure how to isntall a driver... (?ndiswrapper -i driver.sys?)... and then there's getting the ndiswrapper onto a machine without internet connection. Oh well, it's no that far to lay ethernet - as a last resort. Not giving up yet! :D

---

### Post by Simian on 2006-08-03
> **Kulgan said:**
> What does the 's:' in front of the wep do?

The s: in front of the wep key allows you to just enter the pass phrase rather than the actual wep key.

So instead of writing W23R45H1F34K98C4C15HSF5F (blah blah) You could simply write "HOUSE" or "FISH" or what ever you pass phrase is.

---

### Post by Kulgan on 2006-08-03
heh, then it's a pity that I don't know the pass-phrase :p

so normally it should be "wireless-key 2SDFYEEJ65J3HJ63JH3T" and so on?

---

### Post by Kulgan on 2006-08-03
heh, then it's a pity that I don't know the pass-phrase :p

so normally it should be "wireless-key 2SDFYEEJ65J3HJ63JH3T" and so on?

---

