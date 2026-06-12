---
title: "MAC Addresses and Privacy."
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by New101 on 2007-08-15
Hi.

Since installing Ubuntu and buying a router I've become aware of MAC addresses which are apparently hard wired into network cards and cannot be changed?

It's just that I was sitting in a wifi cafe today thinking I was anonymously surfing the net when I realised that if they checked their router's logs they'd see my MAC address and my cover as a covert CIA operative would be blown. 

So my two questions:

1) Does a MAC address uniquely identify your computer?

2) Are MAC addresses visible over the internet in any way?

Thanks in advance!

---

### Post by skymera on 2007-08-15
a CIA?
hmm ok? >_o

a MAC identifies the hardware.

and i think they are visible, just like a IP

---

### Post by zvacet on 2007-08-15
[https://help.ubuntu.com/community/TOR]("https://help.ubuntu.com/community/TOR")

---

### Post by wirelessmonkey on 2007-08-15
Barring a few special circumstances, MAC address cease their outward movement at the nearest router and are generally flushed quickly after you leave the network.
MAC address are burned into the network card, but can be altered in some operating systems (e.g. linux). MAC addresses can be spoofed, and with the right captures, someone knowledgeable could assume the MAC address of another computer and attempt to hijack your connection.  There are many issues with this from a network perspective, and in most conditions the hijack attempt would be mostly worthless so long as your connection is encrypted (DynamicWEP, WPA, WPA2, 802.1x, ssl, etc.) So, unless you're on an unencrypted or Static WEP encrypted network, you shouldn't generally be worried , and if on an unencrypted network there is no incentive to generate such an attack.
IMHO, anyone who is capable of hijacking an encrypted connection will be geared to deal with potential countermeasures, and if you're on a connection using Static WEP, you get what you deserve.

---

### Post by IamAcoconut on 2007-08-18
Ok. Where X is number of the interface (0,1,2 so on) and phony MAC is only an example
```
sudo ifconfig ethX hw ether 00:0R:9G:A5:B7:L1
```
Now, after typing <ifconfig> itself, you'll easily spot hardware addresses of each of your interfaces.

More to come...

---

### Post by nitro_n2o on 2007-08-18
the MAC address associated with layer2 and ASFAIK it won't be propagated after the first hob.. 
I don't think that knowing a mac address of some device is a big threat!!!! and as wirelessmonkey said.. there is no real issues if you are running behind an encrypted connection.. 
anyways.. anonymous surfing is almost impossible!!!!! there is a lot of hidden technologies that can identify you... even when using "anonymity software" These softwares are only helpful to bypass so school filters, companies filters, or parental filters.. 

just an opinion :)

---

### Post by IamAcoconut on 2007-08-18
I assume you are (or should be) worried about data retention. In this case you should start with installing **Tor** in which I can assist you, should you find it difficult. And being concerned with MAC giving you away might be smart too, if it's the ISPs that could cause you trouble (indirectly). If one knows, say, 2 wifi APs you've been to (and when you were there), and can obtain their logs, I guess (please correct me) they can figure out which are yours. 

If you want to stay unknown to the websites you view, use Tor. It can solve a lot of problems if used properly. It won't be enough to just turn it on, if your browser tells the world thay you're running Firefox 2.0.0.6 and Ubuntu 7.4 in Kurdish. Tracking cookies and JavaScript on won't help much either.

Browser identification can easily be altered. There are built in options in Opera, and probably some decent extentions for Firefox (I'll look into that).
Policy towards cookies and JavaScript should be revised. I told my browser not to accept ANY cookies, then given exceptions - trusted sites which need cookies to work properly. Turning off JavaScript may be inconvenient, so you might want to install some FF extention that will give you an off/on button.

> lot of hidden technologies that can identify you
Could you elaborate on this a little? No technology is perfect, and nothing is 100% secure, but does it mean we should stop using firewalls?

---

