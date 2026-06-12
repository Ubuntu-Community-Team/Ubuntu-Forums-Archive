---
title: "Hello from Greece (problem with sound in Imac)"
date: 2010-06-04
forum: Apple Hardware Users
---

### Post by Lisimelis on 2010-06-04
Hello to all from Greece! After seeing in all my computers how good 10.04 was i decided to install ubuntu only on my Imac.Apple iMac "Core 2 Duo" 2.0 20-Inch specs are here

[http://www.everymac.com/systems/apple/imac/stats/imac-core-2-duo-2.0-20-inch-aluminum-specs.html](http://www.everymac.com/systems/apple/imac/stats/imac-core-2-duo-2.0-20-inch-aluminum-specs.html)

everything went smooth and after the wireless and graphics driver installed i was on my way. Thats when i noticed i had no sound. I saw some guides but none seemed to help. Any help here Please....

Thank you in advance...Yiannis

---

### Post by linuxopjemac on 2010-06-04
I don't have a solution for you yet, but it's always good to look how other people solved it.
[http://mac.linux.be/content/sound-problems](http://mac.linux.be/content/sound-problems)

I would advise you to install the alsa backport module for your kernel (synaptic package manager) and to unmute all channels after that with alsamixer (with "m")

If you find a way, tell us. I collect this kind of data.

---

### Post by Lisimelis on 2010-06-04
I Did it !!!!!!!!!!!!!!
i just followed this

[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

on sound problems and all is well....

consider this thread solved!!!

---

### Post by deepee on 2010-06-13
Yep that did the trick! Thank-you everyone. Am new to posting here; two weeks of poking around and I now have iMac21 audio. Now, a question. Is there any work-around the fact that you have to go into Alsamixer on each re-boot and turn the speakers back on? No big problem, but I kinda miss that nice South African log-in sound when logging on.
BTW, I had some issues first few boots with the modprobe .conf modified. Video went to pieces on the first reload, then for some reason neither Chromium nor Firefox wanted to see that we were on-line (Auto eth0 and wireless both were working). Fearing nothing, I restarted the modem a couple of times as well. Now everybody's handshaking.
Here is the line that worked for my 21" alum Mac:
options snd-hda-intel power_save=10 power_save_controller=N model=imac24
Thank-you again! Long live Ubuntu.

---

### Post by linuxopjemac on 2010-06-14
Deepee, can you tel us what iMac code you have? Is it the iMac10,1 ?
What about you Lisimelis?

```
sudo dmidecode -s system-product-name
```

---

### Post by deepee on 2010-06-14
> **linuxopjemac said:**
> Deepee, can you tel us what iMac code you have? Is it the iMac10,1 ?
What about you Lisimelis?

```
sudo dmidecode -s system-product-name
```

Hi, linuxopjemac
It's a 7,1

4 g ram.

Love the hardware, but Snow Leopard drove me back into Ubuntu's arms. I'm running Lucid.

Thanks so much

My last question, has anyone found a workaround to the tinny sound issue? I've hunted numerous Linux sites (not just Ubuntu) and this appears to be a linux-mac issue. Thanking you all in advance.
-d-

-d-

---

