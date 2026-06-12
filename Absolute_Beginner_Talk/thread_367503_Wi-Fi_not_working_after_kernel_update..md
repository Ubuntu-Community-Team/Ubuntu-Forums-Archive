---
title: "Wi-Fi not working after kernel update."
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Frank Golden on 2007-02-22
Hi All,
   Been awhile since I asked for help, so here goes.
I have Edgy installed on a external HDD. Everything worked great including the built in Wi-Fi
(see sig for computer h'ware details). I recently updated to the latest kernel (yesterday)
as well as all the other updates from Update Manager. Now my Wi-Fi doesn't work, Edgy doesn't even see my built in Wi-Fi card. Moving the hardware Wi-Fi switch to on has no effect. The network manager shows no wi-fi card. The odd thing is the Wi-Fi works if I boot the previous kernel? Anyone have any thoughts or ideas how to fix this. I don't have access to wired internet at the motel I am staying at for a couple of weeks, so I am stuck with Wi-Fi. (I am a contractor working at Duane Arnold Nuclear Station here in Iowa.)
I need to access the internet to update my ATi drivers for the new kernel.

Any help would be greatly appreciated. Thanks.

PS. I don't need ndiswrapper. Edgy has native support for my Intel card (the latest Centrino ABG).
There has to be a way to force Edgy to recognize my Wi-Fi card and allow the hardware on/off switch to work
with the new kernel. Unless there is a bug in the new kernel that is.

---

### Post by orb9220 on 2007-02-22
I had this happen before.

For me I had to edit a file.   /etc/network/interfaces

And put "#" comments in front of all the lines except auto lo like this:
> 
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


#iface ath0 inet dhcp
#wireless-essid [www.personaltelco.net](www.personaltelco.net)

#iface ath0 inet dhcp
#wireless-essid [www.personaltelco.net](www.personaltelco.net)


And save then relogon

Hope this helps

---

### Post by Frank Golden on 2007-02-22
> **orb9220 said:**
> I had this happen before.

For me I had to edit a file.   /etc/network/interfaces

And put "#" comments in front of all the lines except auto lo like this:


And save then relogon

Hope this helps
Editing /etc/network/interfaces no help.

---

### Post by linux_kid on 2007-02-22
Unless the kernel update is important to you, I would just uninstall the new kernel from synaptic.

Note: The 2.6.17-11-generic kernel (the one you probably upgraded to) has caused many wifi problems, so just wait for 2.6.17-12-generic.

---

### Post by Frank Golden on 2007-02-22
> **linux_kid said:**
> Unless the kernel update is important to you, I would just uninstall the new kernel from synaptic.

Note: The 2.6.17-11-generic kernel (the one you probably upgraded to) has caused many wifi problems, so just wait for 2.6.17-12-generic.
Thanks Linux_kid. I will just leave it there and uncomment the entry from grub and use the earlier kernel. Can't access the internet from the new kernel to uninstall using synaptic. No wired access from here. Hopefully the .....12 kernel will fix these issues. Edgy, one step forward
and two steps back. LOL

---

### Post by Frank Golden on 2007-02-27
Well turns out all I had to do was install the linux-generic metapackage thru Synaptic to get my Wi-Fi back. Thanks to jdong for the direction.

---

