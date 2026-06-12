---
title: "wlan0/ra0"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by cmfourie on 2006-07-26
I tried installing my wlan card on ubuntu and I couldnt do it, I then went to Kubuntu and it recognised the wlan card. i then configured the network settings, putting in ESSID there is no encryption key and setting dhcp to automatic, as advised in COMPUTER ACTIVE ADVANCED TIPS ISSUE 6 PAGE 80 & 81

My laptop has listed my device as ra0, but when I do a netork search it doesnt pick anything up, even when I am right next to the router.

Any Ideas???

Thanks

---

### Post by Third Thoughts on 2006-07-26
> **cmfourie said:**
> I tried installing my wlan card on ubuntu
Thanks

Can you give us some more details about the card. Make and model number etc. If you don't know off the top you your head, you can use the command lspci to get a list of hardware on your computer. Just copy and paste what you see in the terminal to a new post

~Andrew S.

---

### Post by philippe_carlo on 2006-07-26
You can also try
```
sudo iwconfig wlan0 power on
```

---

### Post by cmfourie on 2006-07-26
the retailer is belkin

the chipset is: RALINK RT 2500 802.11

---

### Post by philippe_carlo on 2006-07-26
what does 'sudo iwconfig' give?

---

### Post by cmfourie on 2006-07-26
lo     no wireless extensions

irda0  no wireless extensions

ra0 RT2500 Wireless ESSID: "BTVOYAGER2100-F6"
    Mode: Managed Frequncy=2.4ghz bit rate 11Mb/s
RTS thr:off Fragment thr:off
Link quality=0/100 Signal level=-120dBm noise level -193 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed Beaco:0



had to type everything out.

---

### Post by cmfourie on 2006-07-26
ra0 RT2500 Wireless ESSID: "BTVOYAGER2100-F6"
Mode: Managed Frequncy=2.4ghz bit rate 11Mb/s
RTS thr: off Fragment thr: off
Link quality=0/100 Signal level=-120dBm noise level -193 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed Beaco:0

---

### Post by Third Thoughts on 2006-07-26
> **cmfourie said:**
> the retailer is belkin

the chipset is: RALINK RT 2500 802.11

You should probably look into using ndiswrapper. According to this site your chipset is support by ndiswrapper.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
Here's the wiki site on setting up ndiswrapper.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
~Andrew S.

---

### Post by cmfourie on 2006-07-26
i have no way of getting ndiswrapper

I only have one connection to internet and that is throgh anothr computer, that does not have a cd writer.

---

### Post by Third Thoughts on 2006-07-26
If you have the Dapper Drake Live CD you can install ndiswrapper from there. Just insert the CD and then boot up synaptic. The only problem you might have it getting the necessary windows drives, but if you have a floppy or usb flash drive they'll probably fit on there.

~Andrew S.

---

