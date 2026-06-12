---
title: "Wireless Troubles"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by mtgrocks04 on 2006-10-29
I recently installed Edgy. At first my wireless worked fine. But now it is not connecting. The wireless utility lists all the available networks correctly but every time I try to connect it says "failed to connect". Any thoughts would be appreciated.

---

### Post by H.E. Pennypacker on 2006-10-29
What application are you using for connecting?  Network Settings doesn't say "failed to connect" when it doesn't connect, so you must be talking about something else.

---

### Post by mtgrocks04 on 2006-10-29
the network settings says that the card the wireless is on. In the internet menu of Kmenu there is a wireless assitant. I go in there and it shows all the connections available on my college campus and it fails to connect to those.

---

### Post by Dual Cortex on 2006-10-29
The wireless Assistand hasn't worked for me either. I've only tried it on one network though.
For now I got my computer 'semi-working' by editing /etc/network/interfaces/

---

### Post by mtgrocks04 on 2006-10-29
what changes did you actually make to /etc/network/interfaces/? i really need to get the internet working so any help at all is greatly appreciated.

---

### Post by Ryupower on 2006-10-30
I'M BUMPING THIS!
*Bump*

Why? Because I have the same problem. 
I'm trying to use Kubuntu Edgy Eft, and it tells me the correct connections, but just doesn't seem to want to connect. I always get "failed to connect" as an answer. The Win2k on the same computer connects, the Ubuntu on my laptop as well. Just Edgy doesn't seem to want to connect. :/

Maybe it's a KDE thing or something. But point is:
Lists networks. I click. Few seconeds later: *failed to connect*. :/

Also, eventhough I type in my password, it gives me " you may not have the permission to connect to networks" or something like that. What's up with that?
Thanks to anyone that can help >us<

---

### Post by orb9220 on 2006-10-30
> what changes did you actually make to /etc/network/interfaces/? i really need to get the internet working so any help at all is greatly appreciated.

You have to comment out all lines except auto lo first line like this.

> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp
#wireless-essid [www.xxxxx.net](www.xxxxx.net)

#auto wlan0
#iface wlan0 inet dhcp


#iface ath0 inet dhcp
#wireless-essid [www.xxxxxx.net](www.xxxxxx.net)

#auto ath0

Hope this helps

---

### Post by mtgrocks04 on 2006-10-30
Worked for me...thanks for the help :)

---

### Post by YoungCthulhu on 2006-10-30
Hi all,
I installed Edgy over the weekend.  Previously, on Dapper, my wireless worked fine, a D-Link 510 PCI card on an old Athlon HP Pavillion 8630 machine.

Wireless card wouldn't work on Edgy, along with the sound card so I finally reverted to a complete re-install of Dapper 6.06, but found that my wireless would no longer connect.  I activated it under System|Networking, configured it for DHCP and it seemed OK but it just wont connect. The power light is on, the activity light flashes about 5x at regular intervals but no luck.

I was wondering if it had anything to do with re-naming my computer, so I did a complete re-install and reverted to the old name.

Still no luck!](*,) 

Any ideas anyone??

Cheers

---

### Post by mtgrocks04 on 2006-10-31
Did you try the stuff from the post up above with the commenting?

---

### Post by YoungCthulhu on 2006-10-31
Thanks for the reply, mtgrocks! No, not yet.  Will do tonight.

Also, our IT help person suggested that the router could be "saturated" in that it only handles 2 wireless computer connections and I should log on and delete one of the previous computers.  Not had much experience with how routers work. Have u had experience with this sort of thing before?

I also looked up what an "Eft" is and found it is a newt in it's immature juvenile state :-k 

Cheers

---

