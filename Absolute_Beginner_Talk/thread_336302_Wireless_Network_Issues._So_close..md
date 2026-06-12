---
title: "Wireless Network Issues. So close."
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by tgdrums1990 on 2007-01-11
Okay. I got everything updated and have it all congigured correctly. But I cant seem to get signal. It has reconised my built in wirless card but says I have no signal. But my wirless newtowrk is working properly. Is this a Ubuntu issue or my router? I know the card works because it worked fine under windows.

---

### Post by stalker145 on 2007-01-11
> **tgdrums1990 said:**
> But I cant seem to get signal. It has reconised my built in wirless card but says I have no signal. But my wirless newtowrk is working properly.

A couple of questions first:

Is your router advertising your network (SSID)?

Have you activated the network interface? This could be called RA0, ATH0, WLAN, and a plethora of other things - just check to make sure.

See, I said a couple ;)  This is where I would start. To activate your wireless card (or check) just open up your network manager (probably in the system tray) and make sure that it's not ETH0 or something like that selected.

Check back if you need more help.

---

### Post by tgdrums1990 on 2007-01-11
Okay. When I was running windows. All I had to do was enter the key because it said it had limited or no internet conectivity but it did reconise the router (stonehendge). 

Under Ubuntu it has not detected any wirless netowrks. And I can activate my ETH1 Wirless card, but once I hit okay and it closes the window, It goes back to not activated. So I am still having issues there. ](*,) 

Do I need to make a new post or do I just keep coming back to the same one? I notice that the board moves fast around here.

---

### Post by LookTJ on 2007-01-11
As far as I've heard, WEP/WPA doesn't work on Linux by default. Try disabling WEP security to make sure it isn't really a Ubuntu issue.

---

### Post by edmund on 2007-01-11
You haven't said what kind of wireless card you have, but I found this useful for my Broadcom card:
[http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)

It could be useful even if you have a different card, e.g. the advice on:
- renaming eth1 to wlan0 in various places.
- connect using the gnome-network-manager, rather than System / Administration / Networking

Also, I have found I can connect to a Network if the network manager prompts for "WPA Personal", but not if it prompts for a "WEP Passphrase".

Hope that helps.

---

