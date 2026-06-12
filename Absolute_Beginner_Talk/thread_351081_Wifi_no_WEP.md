---
title: "Wifi no WEP"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by DrMilo on 2007-02-01
Hi all: I couldn't find this specific problem addressed anywhere. At my university you need WEP disabled to use the wireless network (please spare me the security comments it's not up to me). The network connection setup in Ubuntu never seems to remember this setting. There doesn't seem to be any option in the dialogue to switch it permanently to ASCI instead of hexadecimal and it seems to revert back to hex all the time (after reboot). Also if I connect with Ethernet it wants to do that after reboot even if there’s no Ethernet connected and the Wifi card is inserted (My laptop is old so I insert a PCMCIA card for Wifi and don’t insert it when using Ethernet, in other words, why doesn’t Ubuntu just know what’s connected?) plus wanting to use hex when I switch it to Wifi. I downloaded gtkwifi in the hopes that it would let me tinker with the settings but it actually just seemed to get in the way. Using Ubuntu Dapper. Sure I can switch the setting each time but it's a nuisance. So can anyone suggest either an application I can download that will manage the settings properly or a command line that will make Ubuntu remember/behave? Ideally I want an application that will let me deal with various network setups more robustly (detects connections?) and something that uses a mouse not terminal. Oh and to make it harder on you all I don't know anything about compiling and don't really care to learn! Thanks in advance!

---

### Post by mikewhatever on 2007-02-01
One solution for WiFi could be to use a network manager. I used to have gnome network manager, and was able to connect to both WEP enabled and disabled networks. If you haven't tried one yet, gnome network manager is in Synaptic, or Add/Remove applications

---

### Post by DrMilo on 2007-02-01
Thanks Mike. I've installed it (that could have been easier) it'll take a day  or 2 to see if it is an improvement. I'd like it to show me a more detailed interface initially but  if it works it works.

---

### Post by mikewhatever on 2007-02-01
you're welcome. You can always try another one if you don't like gnome nm.

---

