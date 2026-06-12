---
title: "Netgear WPN311 Linux Device Driver"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by Caldor on 2005-09-18
Gday all

Well Im looking to feel the joy of Linux and Ubuntu seems to be a good choice for the distro........

I have a Netgear PreN wireless NIC, cant find any device drivers for linux. What do I do? Its a model WPN311.

I have a RAID 0 SATA array on my i875 chipset mobo, but Im lead to believe this will be ok. My X800 has Linux drivers and so does my Audigy 2.

Also with the wireless, can I still run WPA encryption?

Thanks

---

### Post by KingBahamut on 2005-09-18
I dont see it on the wlan compat list. 
[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz) 

The MA311 is on there though as a Prism , so the standard Prism driver should work. 

if not

Ndiswrapper is going to be what your going to have to use.

---

### Post by Caldor on 2005-09-18
Thanks. Being a PreN card I dont think it will work with 802.11G type chipsets.

Having a look on the Atheros website, it says the WPN311 has the Atheros AR5004G Chipset.

I dont think ndiswrapper supports this.

Madwifi on sourceforge doesnt list it as compatible either.

---

### Post by KingBahamut on 2005-09-18
hmmmm.....

atheros driver.

Ive never tried to compile it, so I cant speak on that.

---

### Post by ranman on 2005-12-07
Hmm... I am having the same problem I have tried pretty much everthing I can think of but the most I was able to get it to do was detect all the networks, it still can't connect to them though... god this is annoying If anyone manages to figure this out I would be much obliged!

---

