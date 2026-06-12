---
title: "How do I connect myself to the internet?"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by Rosamunda on 2006-04-03
Hi there!
My Ubuntu Live CD has just arrived and I find Linux AMAZING!
Love it already!

My only issue to installing it right away is... how do I connect myself to the web?

My PC connects though a wireless adapter. The router is connected to another machine.

The Installation CD that cames with the little wireless adapter, is configurated (I think) to run in Windows... :-k 

The Wireless Adapter is **DLink DWL-122**
What should I do?

Thanks for your advice!

Rosamunda

---

### Post by taurus on 2006-04-03
Does your wireless work with the LiveCD?  Is that an pci or usb adaptor?

---

### Post by Rosamunda on 2006-04-03
Thanks for your answer Taurus!
It didn´t worked with the LiveCD (I´m gonna try it again anyway), and it is an USB port... How it should be installed?

Thanks again!

Rosamunda

---

### Post by az on 2006-04-03
[QUOTE=Rosamunda]Thanks for your answer Taurus!
It didn´t worked with the LiveCD (I´m gonna try it again anyway), and it is an USB port... How it should be installed?

Thanks again!

Rosamunda[/QUOTE]


You need to install linux-wlan-ng (it is on your cd - just use synaptic)

That device does not integrate with the other wireless tools available.  It goes about things a different way.  You need to edit the /etc/network/interfaces file and configure your card yourself

sudo gedit /etc/network/interfaces

and add this:

iface wlan0 inet dhcp
wlan_ng_key0 xx:xx:xx:xx:xx (where the xx's are your WEP key)
wireless_mode managed
wireless_enc on

auto wlan0
Then save the file and try to active your connection using the networking tool.

Here is the bug report about fixing this:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/21569](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/21569)

---

