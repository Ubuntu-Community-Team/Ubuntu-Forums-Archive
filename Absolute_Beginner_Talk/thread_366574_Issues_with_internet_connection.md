---
title: "Issues with internet connection"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by ladysorka on 2007-02-21
I installed Ubuntu this morning, and I can connect to the internet when directly connected to the modem, but if I try to go through the router, either wireless or wired, I can't connect.  If I monitor the connection, it tells me that it's sending and receiving packets, but it simply won't connect to anything - pages try to load for about three minutes before giving me a 404.  I've tried both wired connected through the modem and wireless (as I can see my network), and it does the same both ways.

It works fine if I connect directly to the modem, but through the router... not so much.  I have a Linksys WRT54G router and an Intel wireless card (though I'm afraid I'm not positive on the exact model, as it came pre-installed).

What should I be doing here?

---

### Post by DSn0wMan on 2007-02-21
It is most likely your router settings. Make sure its set up to give you an address via DHCP. It is also best to test your router settings while connected directly with a cable.

---

### Post by ladysorka on 2007-02-21
Unfortunately, I can't get into the router to modify the settings either - if I try to get into the router, it still does the "try to find it" for about three minutes before giving a 404.  The router was working fine with Windows, so it presumably works, but, uh.  It's not letting me even get into it.

---

### Post by DSn0wMan on 2007-02-22
Hmm.. I guess the first thing to determine is how you connected to it before. Was it a static IP or DHCP? Then post your "/etc/network/interfaces" file so if there are any errors in there we can weed them out.

---

### Post by luke411 on 2007-02-22
I have the same router and I have had similar problems. It is most likely the same DHCP issue that I have, though we have different NIC cards. I also have a desktop Ubuntu on the same network that would cause me the same problem. The only work around I have found was to assign static IP's to all of my pc's on this network (including the two windows pc's) and the problem went away. I think Ubuntu does not always get a renewed IP address from the router, or at least my router, each time it is booted and it tries to use the same IP address as it did last time. Of course, by then, the IP address is probably being used by one of my other three pc's and is not available so it would show connected, packets moving in and out and finally I would get an error.

I still have issues similar to that using wireless, in that I sometimes have to 'force' my laptop to set up a new network configuration after I reboot it. I usually do this in the Network settings in Sytem-Administration and assign a different IP address to it (one that I know is not assigned to my other pcs) and voila, I'm connected again.

I don't understand why the wireless is acting that way when the IP address I gave it should still be free and available even after I reboot the machine and it doesn't always do it after reboot, it's hit and miss. But in all cases, it tells me packets are going in and out. 

I'm not sure any of this helps you except to say that you may have to try different configurations between the router and the pc and that if it's like mine, it's an on going work in progress even when it does work. I am confident though that it is a DHCP issue with this particular router and the way it assigns IP addresses.

---

### Post by netkid91 on 2007-02-22
Please type the output of ifconfig run through the terminal here.

---

