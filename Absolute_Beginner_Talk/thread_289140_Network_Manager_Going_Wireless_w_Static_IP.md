---
title: "Network Manager Going Wireless w/ Static IP"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-10-30
I have seen many people wondering how to get static IP addresses in Network
Manager and I couldn't find a good answer on these forums. It seems Ubuntu's
network setup makes it a little difficult to workaround the lack of features
in Network Manager as well..

My question is, does anyone know how to have a static IP address with one 
network and not all the others I connect to at different times? I found [this]("http://ubuntuforums.org/showpost.php?p=1032858&postcount=1")
 thread, but it's a little over my head and it's going for a wired network.

If you have any suggestions, that would be great!

---

### Post by netztier on 2006-10-31
> **shanepardue said:**
> 
My question is, does anyone know how to have a static IP address with one 
network and not all the others I connect to at different times? 

I sometimes use an unencrypted WLAN with an access list for MAC-Addresses and no DHCP service available. In **[COLOR="Red"]Dapper[/COLOR]**, what I did was this (**ath0** being my wireless interface):

[LIST]
[COLOR="Gray"][*]"disable Wireless" in Network-Manager
[*] fake my MAC-address with macchanger: [FONT="Courier New"]**sudo macchanger -m 11:22:33:44:55:66 ath0**[/FONT]
[*] "enable Wireless" in Network-Manager.[/COLOR]
[*] wait until DHCP client times out and assigns an APIPA address (RFC3330) from the 169.254.0.0/16 range
[*] add a second address to a subinterface of ath0: **[FONT="Courier New"] sudo ifconfig ath0 add 192.168.0.102 netmask 255.255.255.0 broadcast 192.168.0.255[/FONT]**
[*] add a new default route, across the newly created subinterface **ath0.0**, pointing to the right default router for this network: **[FONT="Courier New"]sudo route -v add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.0.1 dev ath0:0[/FONT]**
[*] Copy a hand-crafted resolv.conf (containing the right DNS Server IP addresses for this network) over the existing one to have name resolution: [FONT="Courier New"]**sudo cp /etc/resolv.staticnetwork /etc/resolv.conf**[/FONT]
[/LIST]

This of course is completely uncomfortable (although possibly scriptable), but it allows for continuing to use network manager with WEP, WPA etc in the other WLANs I use.

Now in **[COLOR="Red"]Edgy[/COLOR]**, the part with RFC3330 and the 169.254.0.0-address fails. The interface remains "down" and I cant' assign it another address on the subinterface, so I'm kind of stuck here.

I'll have to investigate...

regards

Marc

---

### Post by shanepardue on 2006-10-31
my only problem is, my router is on it's last leg and it isn't assigning IP addresses. DHCP is enabled and all that..I've been through linksys' forums for awhile and there was no solution. I need a new router, but in the meantime, I must have an IP address manually entered Thank you for the suggestion though.

---

### Post by featherking on 2006-11-08
Network manager doesnt support Static IP's. It probably wont until the 0.7 release. On their mailing list they frequently talk about this, i would consider signing up for their mailing list for more info. Check them out at [http://www.gnome.org/projects/NetworkManager/]("http://www.gnome.org/projects/NetworkManager/")
Towards the bottom of the page you can browse the mailing list archives

good luck

---

### Post by shanepardue on 2006-11-08
> **featherking said:**
> Network manager doesnt support Static IP's. It probably wont until the 0.7 release. On their mailing list they frequently talk about this, i would consider signing up for their mailing list for more info. Check them out at [http://www.gnome.org/projects/NetworkManager/]("http://www.gnome.org/projects/NetworkManager/")
Towards the bottom of the page you can browse the mailing list archives

good luck
Yeah, I have since signed up for the mailing list, but it looks like I may 
have to wait for the next release. Ubuntu has specific networking issues that
 conflict with the configuration of a static IP with NM. Thanks for your 
help!

---

### Post by wieman01 on 2006-11-10
If you can live without NetworkManager & a GUI, then you could try this instead: [http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

---

