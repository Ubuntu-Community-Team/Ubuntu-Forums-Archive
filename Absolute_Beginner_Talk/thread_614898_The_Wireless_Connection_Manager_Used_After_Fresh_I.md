---
title: "The Wireless Connection Manager Used After Fresh Install"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by ryank on 2007-11-16
dear knowledge-filled ubuntu forum members,

i tried ubuntu out a while ago and was having no luck at all getting my wireless card to work.  after countless problems with windows, i decided to give it a shot once more.  i was astonished when i realized my wireless card was natively supported with 7.10.  the second i booted up, i had a wireless connection!

there are going to be a few skeptics out there when i type my next few lines.  for the past three or four months, my room mates and i have had permission from our neighbor/friend to use his unsecured wireless connection.  we've been connecting to this with ease since ever he ALLOWED us.

with that out of the way...

after ubuntu booted for the first time and my wireless card was detected, i connected to this unsecured connection with no problem at all using the wireless connection manager that ubuntu uses during the first boot.  the one i refer to (an icon with two little balls) is completely different than the network manager (the one with two computer monitors) that is on my panel now.  i had no problems whatsoever connecting to the unsecured network with the manager with the two-ball icon and i'm having no luck at all connecting to this unsecured network with the two-monitor manager.

this is probably completely obvious, but there's something i'm overlooking and it's driving me nuts!  help me bring back the two-balled icon!

PLEASE HELP ME.  YOU WILL FOREVER BE IN MY DEBT!

ryank

---

### Post by Inxsible on 2007-11-16
the "two little balls" (pun intended ;) ) and the two computer icons are one and the same application called nm-applet.

When you have the 2 computers, it means that you have connected a wired internet connection. Or if you also have a small red 'X' mark near the computers, it means that it is not connected to any internet connection (wired or otherwise)

If you haven't connected an ethernet cable, then single click on the icon and you will see a list of available networks that you can connect to. Supply the network password if any and see if it connects.

---

### Post by ryank on 2007-11-16
see, i knew it was obvious.  thanks for the really quick response.

i have gone into the properties.  the wireless connection shows up in the drop down list, but i'm not sure how i go about connecting to it as it's unsecured.  i've tried enabling roaming (which i'm pretty sure was selected when i first booted) to no avail.  i've tried connecting manually with these options under "wireless settings":

essid: SassyNET
password type: wep (hex)/wep (ascii)/wpa personal/wpa personal 2
password: always leave this one completely blank

and under "connection settings":

configuration: always use automatic configuration (dhcp)

any recommendations on re-trying one of those or any completely new suggestions are more than welcome.

thanks!

---

### Post by Evil Wayz on 2007-11-23
> **Inxsible said:**
> the "two little balls" (pun intended ;) ) and the two computer icons are one and the same application called nm-applet.

When you have the 2 computers, it means that you have connected a wired internet connection. Or if you also have a small red 'X' mark near the computers, it means that it is not connected to any internet connection (wired or otherwise)

If you haven't connected an ethernet cable, then single click on the icon and you will see a list of available networks that you can connect to. Supply the network password if any and see if it connects.

I reloaded nm-applet, but i still dont' ge the two balls. I also still dont have an option to switch between a wired network and a wirelss network.  I have to set it manually. IT defaults to wirelss for some reason.

---

