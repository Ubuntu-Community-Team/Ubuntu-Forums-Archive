---
title: "Cant configure wireless"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by MeMosh on 2007-02-28
Hi, this is my first try with linux, i just installed ubuntu 6.06 and so far everything is fine,

The only problem is that i cant get the wireless card to work, im using a Thinkpad R60e laptop. About the card, the console said:

> Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)


i read a wiki about [how to install ubuntu in a R60e](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e#Wireless) and it said:

> You need to install linux-restricted-modules-generic, which contains the kernel module ath_pci. ath_pci is loaded automatically at system startup.

I did that with the synaptic package manager, and selected the one for my kernel (2.6.15-26-386).

I guess i need to do something else because i cant see the wirless card in the Network settings

[[IMG]http://img339.imageshack.us/img339/6765/screenshotnetworksettincu6.th.jpg[/IMG]](http://img339.imageshack.us/my.php?image=screenshotnetworksettincu6.jpg)

Sorry for the trouble, this is my 3rd day with ubuntu or any linux distribution, i apreciate your patience and, thx in advance :KS

---

### Post by jimrz on 2007-02-28
> **MeMosh said:**
> Hi, this is my first try with linux, i just installed ubuntu 6.06 and so far everything is fine,

The only problem is that i cant get the wireless card to work, im using a Thinkpad R60e laptop. About the card, the console said:



i read a wiki about [how to install ubuntu in a R60e](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e#Wireless) and it said:



I did that with the synaptic package manager, and selected the one for my kernel (2.6.15-26-386).

I guess i need to do something else because i cant see the wirless card in the Network settings

[[IMG]http://img339.imageshack.us/img339/6765/screenshotnetworksettincu6.th.jpg[/IMG]](http://img339.imageshack.us/my.php?image=screenshotnetworksettincu6.jpg)

Sorry for the trouble, this is my 3rd day with ubuntu or any linux distribution, i apreciate your patience and, thx in advance :KS

did you reboot your system after installing the restricted modules? if not, that should get your card going. it is madwifi in the restricted modules that your card will use. never had any problem with the a/b/g wireless on my T42, Atheros chipset,  under dapper (or breezy or edgy) using madwifi restricted module

---

### Post by MeMosh on 2007-02-28
Yeah i did reboot it, but the system>admin>networking window shows the same, i just cant see the card there.

---

