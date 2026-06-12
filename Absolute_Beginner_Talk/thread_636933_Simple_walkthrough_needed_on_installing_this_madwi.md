---
title: "Simple walkthrough needed on installing this madwifi patch"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Jeztastic on 2007-12-10
> 
Originally Posted by DemonBob 
Madwifi Patch for this card: [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
Madwifi Other Card Thread: [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Patch was removed from Madwifi due to API Breakage on non I386/686 platforms. I was able to grab a new link to it from #eeepc channel

Download, source + patch [http://quaggaspace.org/eee/madwifi-eee.tar.bz2](http://quaggaspace.org/eee/madwifi-eee.tar.bz2).

It does work.

Madwifi is talking to Athero's about getting this working across all platforms, and included in an offical release. Right now it only works on i386 and not x64. It does work on Acer 5315.

Please could I get a step-by-step on haw to install this? I'm sorry, but I'm a total n00b, and a lot of this stuff is beyond me. Not even sure if I have midwifi. I tried to download it, but you have to compile it and it looks pretty complex. 

I tried asking this question in [this thread]("http://ubuntuforums.org/showthread.php?t=512828&page=24"), but no replies... 

Many thanks.

---

### Post by stchman on 2007-12-10
> **Jeztastic said:**
> Please could I get a step-by-step on haw to install this? I'm sorry, but I'm a total n00b, and a lot of this stuff is beyond me. Not even sure if I have midwifi. I tried to download it, but you have to compile it and it looks pretty complex. 

I tried asking this question in [this thread]("http://ubuntuforums.org/showthread.php?t=512828&page=24"), but no replies... 

Many thanks.

Did you try enabling the Restricted driver in the Restricted Drivers Manager?  If you did and that did not work give my madwifi script a try.  It was originally intended for Feisty but should work for Gutsy.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

Go to the Scripts section and download the Madwifi for Feisty script.  You will need to chmod 755 the script and run as root.

---

### Post by Jeztastic on 2007-12-10
Yes I did, and RDM told me the drivers were working. However, I could not access the internet, and there was nothing else to say they were working. I think the version is too new. Do you think that I could have used the card with the Restricted driver all along but didn't realise?

I since tried to enable the card using some code for Ndiswrappers, and it appears to not be working anymore. I think I disconnected or uninstalled them, as I didn't know what I was doing.

Thanks for the link, I will try it tomorrow evening.

Jez

---

### Post by Jeztastic on 2007-12-11
Hi. 

This hasn't worked for me. I followed all the steps, and they ran OK - no error messages. However, on reboot, no WiFi.

The modules file came out as...

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ndiswrapper
ndiswrapper


ath_pci
```

What now?

---

