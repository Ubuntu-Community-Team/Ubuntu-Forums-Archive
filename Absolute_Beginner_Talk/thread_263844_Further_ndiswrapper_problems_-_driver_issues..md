---
title: "Further ndiswrapper problems - driver issues."
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-09-23
Okay. So in order to get this internet business working, I had to take my computer downstairs and plug it in in place of my sister's computer. I've got all that ndiswrapper and ndiskgtu or whatever installed and working, but whenever I try to activate the wireless internet, my computer freezes. Upon checking the windows wireless drivers section, I have seen that it says "Device connected: No"

I assume I need to use a different driver -- I was using the one from my CD that I got with the adapter. It is a Linksys Wireless-G USB Network Adapter, model number WUSB54G.

Another thread said to use "r2x00" drivers (or something to that effect), but upon downloading those, I cannot locate a .inf file.

Does anyone know what the problem is, and furthermore how to fix it?

---

### Post by blx_286 on 2006-09-23
> **theknave said:**
> Okay. So in order to get this internet business working, I had to take my computer downstairs and plug it in in place of my sister's computer. I've got all that ndiswrapper and ndiskgtu or whatever installed and working, but whenever I try to activate the wireless internet, my computer freezes. Upon checking the windows wireless drivers section, I have seen that it says "Device connected: No"

I assume I need to use a different driver -- I was using the one from my CD that I got with the adapter. It is a Linksys Wireless-G USB Network Adapter, model number WUSB54G.

Another thread said to use "r2x00" drivers (or something to that effect), but upon downloading those, I cannot locate a .inf file.

Does anyone know what the problem is, and furthermore how to fix it?

I am a noob and I am working on the same problem. I am trying to setup ndiswrapper for an Airlink AWLC5025 card. Similar problem, different cards.

If you plug the card in, go into terminal and type ```
lsusb 
``` what do you get?

I think we need to find out what your chipset is first, to determine which drivers you need to install.

Also, what exactly did you download for drivers?

---

### Post by theknave on 2006-09-23
I went back to my CD and got a different driver version off of them (I was trying to use V4). V2 works, and the graphical interface for ndiswrapper says that the defice is connected, but my computer still freezes when I try to enable the wireless connection.

Here is the information you requested:

brett@Brett:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 049f:000e Compaq Computer Corp. Internet Keyboard
Bus 001 Device 002: ID 13b1:000d Linksys
Bus 001 Device 001: ID 0000:0000
brett@Brett:~$

Any help would be appreciated.

---

### Post by blx_286 on 2006-09-23
> **theknave said:**
> I went back to my CD and got a different driver version off of them (I was trying to use V4). V2 works, and the graphical interface for ndiswrapper says that the defice is connected, but my computer still freezes when I try to enable the wireless connection.

Here is the information you requested:

brett@Brett:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 049f:000e Compaq Computer Corp. Internet Keyboard
Bus 001 Device 002: ID 13b1:000d Linksys
Bus 001 Device 001: ID 0000:0000
brett@Brett:~$

Any help would be appreciated.

Ok, I think we are now at the same place, even though we have two different cards. I don't know if it's a driver prob or if maybe something needs to be blacklisted.

Try going into >System >Administration >Device Manager and locate your wi-fi card. There should be some info there on the chipset. Once you find that, post it and maybe someone with the same card can help out.

You might also try searching the forum with the chipset info, once you find it.

---

### Post by theknave on 2006-09-23
> **blx_286 said:**
> Ok, I think we are now at the same place, even though we have two different cards. I don't know if it's a driver prob or if maybe something needs to be blacklisted.

Try going into >System >Administration >Device Manager and locate your wi-fi card. There should be some info there on the chipset. Once you find that, post it and maybe someone with the same card can help out.

You might also try searching the forum with the chipset info, once you find it.

I just tried that and then realized that I don't know what chipset info is.

---

### Post by blx_286 on 2006-09-23
> **theknave said:**
> I just tried that and then realized that I don't know what chipset info is.

Ok I think this will work, go back into terminal and type```
dmesg
```

Then post the output back here. When you post it, click on the little pound sign icon. This will put in a section that says code in []. Paste your text in the code section.

---

### Post by blx_286 on 2006-09-23
> **theknave said:**
> Okay. So in order to get this internet business working, I had to take my computer downstairs and plug it in in place of my sister's computer. I've got all that ndiswrapper and ndiskgtu or whatever installed and working, but whenever I try to activate the wireless internet, my computer freezes. Upon checking the windows wireless drivers section, I have seen that it says "Device connected: No"

I assume I need to use a different driver -- I was using the one from my CD that I got with the adapter. It is a Linksys Wireless-G USB Network Adapter, model number WUSB54G.

Another thread said to use "r2x00" drivers (or something to that effect), but upon downloading those, I cannot locate a .inf file.

Does anyone know what the problem is, and furthermore how to fix it?

I googled your card and there is conflicting info on it [http://www.linux-wlan.org/docs/wlan_adapters.html.gz]("http://www.linux-wlan.org/docs/wlan_adapters.html.gz") says that your chipset is prism.

But [http://www.linuxquestions.org/hcl/showproduct.php?product=3478&cat=all](http://www.linuxquestions.org/hcl/showproduct.php?product=3478&cat=all) says that your chipset may be an Ralink chipset, which is where the r2x00 came from.

I also have the problem with my card locking up my laptop when I try and activate it and I have the Ralink chipset. If I don't use ndiswrapper, the card sets up as RA0, which would be the Ralink chipset. If I use ndiswrapper and the Windows .inf file it sets up as RT61, which is also the Ralink chipset.

So, we may have the same chipset and the same problem.

---

### Post by blx_286 on 2006-09-23
> **theknave said:**
> Okay. So in order to get this internet business working, I had to take my computer downstairs and plug it in in place of my sister's computer. I've got all that ndiswrapper and ndiskgtu or whatever installed and working, but whenever I try to activate the wireless internet, my computer freezes. Upon checking the windows wireless drivers section, I have seen that it says "Device connected: No"

I assume I need to use a different driver -- I was using the one from my CD that I got with the adapter. It is a Linksys Wireless-G USB Network Adapter, model number WUSB54G.

Another thread said to use "r2x00" drivers (or something to that effect), but upon downloading those, I cannot locate a .inf file.

Does anyone know what the problem is, and furthermore how to fix it?

This thread may have what you need, give it a look [http://ubuntuforums.org/showthread.php?t=192588&highlight=rt61](http://ubuntuforums.org/showthread.php?t=192588&highlight=rt61)

---

### Post by blx_286 on 2006-09-24
Not sure if that other link helped but, I found the fix to my prob by following the directions in this thread [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

My chipset is by RaLink and the drivers are RT61.

---

