---
title: "Wireless LAN worked in Edgy but not in Feisty"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-27
I just made a clean install of Kubuntu Feisty from the live cd and tried to connect to a wireless LAN connection using KWirelessManager. It was stuck at 28% of connecting which was "Activation stage: Configuring device" and was unable to connect. Feisty properly detected my wireless LAN card and the wireless router, but was not able to connect.

I tried to boot with Ubuntu (GNOME desktop) Feisty live CD and I was also unable to connect.

I have another partition where I installed Ubuntu and Kubuntu Edgy. I then upgraded to Feisty and I was able to connect. Maybe, just maybe, it is because of my old apps like wireless LAN assistant for KDE in Edgy and the wireless lan app for GNOME in Edgy, I was able to connect.

How do I connect to wlan in Feisty?

---

### Post by Kobalt on 2007-04-27
> **wersdaluv said:**
> Maybe, just maybe, it is because of my old apps like wireless LAN assistant for KDE in Edgy and the wireless lan app for GNOME in Edgy, I was able to connect.

How do I connect to wlan in Feisty?
It is exactly true I think : Fesity uses a new application for networking called Networ-manager. On certain hardware it gets weird results (like on mine) and is unable to connect properly. You can remove it from Synaptic/Adept searching for *network-manager-gnome* & *knetwork-manager* for Gnome and KDE respectfully. Then you can add the good old network-monitor applet to your panel and configure your network just like Edgy did...

---

