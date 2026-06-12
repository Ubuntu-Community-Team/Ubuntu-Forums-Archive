---
title: "Wireless USB Drivers"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by mwebb90g60 on 2006-03-29
Ok, just like everyone else posting here im a Ubuntu noob. I just installed it about 2 hours ago on a laptop which previously had Win 2000 (if it matters). Problem is I cant get it online, because I cannot manage to figure out how to install the drivers from the cd to the computer. Its for a linksys wireless usb adapter. Everything shows its for windows and will fail to run. I found the drivers on the disc, but cannot figure out how to install them. What am I missing? Any help would be appreciated, thanks.

---

### Post by moffa on 2006-03-29
Usually the drivers install automatically.  Try going to a console and typing in:

iwconfig

and post the results

---

### Post by mwebb90g60 on 2006-03-29
"lo        no wireless extensions.

sit0     no wireless extensions."

I tried to ejected and placed the disc back in to see if it would autorun or auto install but nothing happened all it did was open the disc and display its content. Before anyone asks the adapter is plugged in and the lights are lit.

---

### Post by mwebb90g60 on 2006-03-29
Hope that was alright, I cant really copy/paste because I cant get that computer online. Any other ideas, thanks again.

---

### Post by Papa-san on 2006-03-29
If you can get that system hooked up with a cat 5 (wired) connection with your router, you should be able to get it online. I don't know if this is possible. Usually the wireless will show up through iwconfig as 'wlan0' If you can hook up the ethernet, it will show up as 'eth0'.

If you can compile information about the manufacturer of the wireless card it would be helpful. 
This site should be a good starting point:

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29](https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29)

---

### Post by mwebb90g60 on 2006-03-29
Well the problem is the laptop has a NIC bought its not functioning and I dont have the drivers for it anyways so I have to use the wireless USB at this point.

---

### Post by Papa-san on 2006-03-29
Hmmmm... I am not exactly sure what to do then, as I am pretty new as well. I managed to get my wireless working, but had the NIC functioning first... I am sure some of the more experienced users will be able to point you in the right direction. anyways, the link in the post should help narrow it down...

---

### Post by mwebb90g60 on 2006-03-30
Bump, for any more info or help.

---

### Post by nickj6282 on 2006-03-30
Ok, as for installing the drivers from the CD, those are probably Windows only. Chances are your USB wireless adapter won't work, but I'd try searching for the specific model on [http://www.google.com/linux](http://www.google.com/linux) or [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/). Your best bet is an Atheros based Wifi card, which can be had inexpensively (many D-Link cards are Atheros chipset cards).

good luck
-Nick

---

### Post by thomasx on 2006-03-30
Check this out, I was in your situation last night. I'm a total noob but I found this...

Use ndiswrapper to "wrap" the windows driver. Theres a gui utility called ndisgtk that makes it super easy. 

First of all add the ubuntu breezy badger repository in SPM. Then look for ndiswrapper and ndisgtk, mark them for install and apply. Then look in System>Admin and at the bottom you should have something like Windows Wireless Drivers

Follow the steps, activate wlan0 under networking and you should be good to go.

Im still really new, so hopefully this works.

---

