---
title: "Wireless Configuration SSID selector not working"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Escanor Tanthul on 2007-03-06
Over the weekend I had installed 6.06Dapper and my wireless configuration was working fine, I could drop down the SSID Tab to select the network I wanted to connect to.

I reinstalled to 6.10Edgy and that function no longer works, I have to manually enter the SSID instead of being able to select from a dropdown menu.

HAs anyone encountered this before? My Wireless works fine, but that portion of the configuration tool seems to be hosed :(

Any Help would be appreciated!

---

### Post by superm1 on 2007-03-07
> **Escanor Tanthul said:**
> Over the weekend I had installed 6.06Dapper and my wireless configuration was working fine, I could drop down the SSID Tab to select the network I wanted to connect to.

I reinstalled to 6.10Edgy and that function no longer works, I have to manually enter the SSID instead of being able to select from a dropdown menu.

HAs anyone encountered this before? My Wireless works fine, but that portion of the configuration tool seems to be hosed :(

Any Help would be appreciated!
By SSID tab, you mean network-manager?  Or System->Administration->Networking? 

I've never had system->administration->networking working for me.  Network manager on the other hand worked wonderfully on dapper, edgy, & feisty.

---

### Post by tsanoff on 2007-03-07
i am having the same problem, wierd.

---

### Post by placidoaps on 2007-03-09
Same problem here.
If i use the following command line I can see the SSID list

**sudo iwlist scan**

but not not with the grafical network tool... I just have to write it by name...

Any solution?

---

### Post by honns on 2007-03-09
if you want, you could go to the add/remove applications and download Network Selector it finds all available wireless networks and you can save the password too

---

### Post by happy-and-lost on 2007-03-09
I'd recommend using a combination of the Gnome network monitor applet (not network-manager) and wifi-radar. Works perfectly.

---

### Post by tsanoff on 2007-03-10
I downloaded the network-manager 0.6.3, it works flawlessly, it will come as default on the feisty release. (don't forget to disable the wireless device through the networking tab under system->administrator, because you can't have them both claiming the same device)

---

