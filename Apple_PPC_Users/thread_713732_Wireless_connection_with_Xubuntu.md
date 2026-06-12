---
title: "Wireless connection with Xubuntu"
date: 2008-03-03
forum: Apple PPC Users
---

### Post by crod38 on 2008-03-03
I had an old PowerMac g4 (450Mhz, 20 gb hd) that wasn't working properly and decided to install xubuntu 7.04  to see if I could give it a new life. The installation worked perfectly and now I was wondering how I can get wireless on this computer. I have a netgear wg111v2 wifi dongle lying around. Would I be able to use this dongle with my version of xubunu? Any help is appreciated.

---

### Post by benjgvps on 2008-03-03
Your wireless adapter is very likely to be supported, 7.04 has very good Wifi support now. I got my Datel Wifimax to work on my iMac G3 350 with no work at all, I just plugged it in and went to the network control panel and saw that there was a wireless adapter hooked up to my computer. Just write down your network name because I couldn't scan to get a list of networks. Though my network name and password were not to hard to forget. If I do remember correctly that network adapter uses the same chipset that mine uses: ZD1211.

---

### Post by prshah on 2008-03-03
NetGear WG111v2 will have to be used via NDISWrapper, ie, it will use the windows drivers. The problem is, the NetGear CD does not carry the necessary INF files in the open. 

What you have to do is, setup the CD on any other Windows system, then open the "Program Files/NetGear" (or whatever) folder, and within that you will find a folder called "driver" with the required INF files. Copy these inf files, and then use them with NDISwrapper and your original CD on your linux system.

IMPORTANT: installing Netgear software on Windows XP will DISABLE fast user switching. To restore this ability, uninstall the netgear s/w or search the registry for the code "gina" or "msvgina" and remove the lines found. (Probably somewhere in the WinLogon branch, not sure).

The simplest thing to do is to pick up a cheap PCI wifi adapter based on the "Atheros" chipset (I use "Compex" brand). Atheros is supported out-of-the-box-with-zero-configuration, though you have to enable restricted driver support.

While you're at it, why not get XUbuntu 7.10?

Cheers,
PRShah

---

### Post by sennep on 2008-03-03
> **prshah said:**
> 
IMPORTANT: installing Netgear software on Windows XP will DISABLE fast user switching. To restore this ability, uninstall the netgear s/w or search the registry for the code "gina" or "msvgina" and remove the lines found. (Probably somewhere in the WinLogon branch, not sure).

Lol, I remember that. It was so annoying, fortunately you can also download a fix for it.:)



**crod38**:  The Wg111v2 might work without ndiswrapper, some people have been able to do that (just plug it in and see if it works), on my computer it didn't work, but after learning about ndiswrapper and downloading a working driver, I got it to work. I wrote a guide specifically for the WG111v2, it's a link to it in my signature. The guide also has some links to extracted drivers so that you don't have to install it on Windows first.

---

### Post by crod38 on 2008-03-04
I was under the impression that NDISWrapper was only for x86 based systems. How can I get it to work with PPC?

---

### Post by sennep on 2008-03-04
> **crod38 said:**
> I was under the impression that NDISWrapper was only for x86 based systems. How can I get it to work with PPC?

I didn't think about that:(  I've only seen ndiswrapper for x86 and amd64, so I guess it won't work on ppc.

I know some people have been able to get the WG111v2 working without ndiswrapper, in 7.10 at least, not sure about 7.04, and I have no clue if any of those people used a ppc.

I know one guy got it working by setting his router to 128bit WEP. I've also heard that it's important that your SSID is not hidden.

If I were you, I would just plug it in and see if it works, and try some different settings if it doesn't (manually configure connection).

If that doesn't work (and you have lot's of time and patience), you can try to connect manually through the command line, since this is a good way of troubleshooting. [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Be aware (if you're going to use the guide I linked to above) that there are different versions of the WG111v2, and at least one of them uses the RTL8187 driver. You can tell which one you have by typing ```
lsusb
``` in the terminal. If the output contains 0846:6a00 you have a version that uses the RTL8187 driver.

---

