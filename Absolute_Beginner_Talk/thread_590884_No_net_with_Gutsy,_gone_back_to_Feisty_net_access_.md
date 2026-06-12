---
title: "No net with Gutsy, gone back to Feisty net access within 5 minutes!!!"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by k3lt01 on 2007-10-25
Hi all.

I have only been using Ubuntu for a few weeks. Feisty was easy and I downloaded and installed Gutsy thinking it would be to. Been playing with it for a week trying to get net access to no avail. Re-install Feisty and have my net back withing 5 minutes.

I will be staying with Feisty until there is a bit of time behind Gutsy and it is proven to work with my wireless card. I don't know the difference between the 2 that make it SO HARD (actually impossible) to get net access on the new one and SO EASY on the older one but there must be some drastic changes somewhere.

---

### Post by Joeb454 on 2007-10-25
Funny. I couldn't get wireless working in Fiesty, although it recognised the Wireless card, it had poor WPA support.

Gutsy fixed all that and now my wireless works without a hitch!

---

### Post by k3lt01 on 2007-10-25
I'm glad it works for you now in Gutsy, Unfortunately I couldn't afford anymore time trying to get mine working so I had to go back to Feisty. All in all I like Gutsy but I have to be able to access the network and internet so it couldn't stay.

If anyone gets it working with an InProComm IPN2220 wireless card let me know how you did it and I will swap back again as soon as is humanly possible. Until that day its Feisty for me.

---

### Post by michael003 on 2007-11-23
I had this same problem. I describe how I solved it in this post: [http://ubuntuforums.org/showpost.php?p=3823299&postcount=4](http://ubuntuforums.org/showpost.php?p=3823299&postcount=4).

---

### Post by k3lt01 on 2007-11-23
> **michael003 said:**
> I had this same problem. I describe how I solved it in this post: [http://ubuntuforums.org/showpost.php?p=3823299&postcount=4](http://ubuntuforums.org/showpost.php?p=3823299&postcount=4). Not trying to bag you out here but I am not sure you really solved it all that well, you even admit to it being unreliable.
> **michael003 said:**
> We eventually go it working by installing the kernel from Feisty (version 2.6.20-16) and using the drivers for the Linksys WPC54Gv4. It didn't work very reliably however -- the connection kept freezing and had to be restarted. My friend eventually gave up on Ubuntu because of this. Thanks anyway.

---

### Post by MegaJim on 2007-11-23
> **k3lt01 said:**
> Not trying to bag you out here but I am not sure you really solved it all that well, you even admit to it being unreliable.
 Thanks anyway.

I have that same wireless chip on my laptop

Using the old kernel works, but you don't need to roll back to feisty; it isn't the distro thats at fault its some compatibility problems between the new kernel and Network Manager I believe

The solution is to switch to WICD - if you have any problems I can send you a copy of the driver that I know works.

good thread on switching to WICD here: [http://ubuntuforums.org/showthread.php?t=527488](http://ubuntuforums.org/showthread.php?t=527488)

note: it doesn't yet have VPN support, but the devloper expects to release a version with this in the coming future.

---

### Post by k3lt01 on 2007-11-23
> **MegaJim said:**
> I have that same wireless chip on my laptop

Using the old kernel works, but you don't need to roll back to feisty; it isn't the distro thats at fault its some compatibility problems between the new kernel and Network Manager I believe

The solution is to switch to WICD - if you have any problems I can send you a copy of the driver that I know works.

good thread on switching to WICD here: [http://ubuntuforums.org/showthread.php?t=527488](http://ubuntuforums.org/showthread.php?t=527488)

note: it doesn't yet have VPN support, but the devloper expects to release a version with this in the coming future.
I would gladly accept the driver you have.

I have already used WICD once, mentioned it in another thread asking for help with the issue, and it didn't help at all. But I am willing to give it another go with another driver.

Thanks for the info, it is much appreciated.

---

