---
title: "wireless craziness?"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by rasellers on 2008-04-03
OK, here's the deal...
Running Ubuntu 6.06 on a Toshiba Sattelite laptop...everything seems to work smoothly...except the wireless connection.
I know that the wifi card at least works, as it works perfectly fine at my coffee shop.
however, at home, I cannot seem to get it to work.

I don't really understand a lot about networking or whatever, so it may be that's the problem. Or would updating to a newer version fix this?

thanks--if you need any more information...i'll try.

---

### Post by pseudo-random on 2008-04-03
I'd say your coffee shop has a different type of wifi connection than your home.
I'm assuming you've got WPA-PSK at home? Your coffee shop is probably open (unencrypted).
For WPA you'll need wpa_supplicant. Examples are in ```
man wpa_supplicant
```

---

### Post by wolfodonnell9000 on 2008-04-03
So you are able to connect at a coffee shop but not your house? Have you setup your adapter to connect with security enabled? After that I would guess it's your router and not your adapter, however I wouldn't be the one to talk with about that.

---

### Post by Hospadar on 2008-04-03
Is there a difference in setup between coffe shop and work? Like for example the coffe shop doesn't have a password but your home network does?  Sometimes certain features (like WPA and WEP network encryption) arn't supported (well or at all) on certain wireless cards.

If this isn't an old installation with tons of stuff on it, I would first suggest just installing the new version (7.10 or even the 8.04 beta, it's pretty stable, and worth a try).  If it's an old machine with performance limitations, try using xubuntu.

That said, if you don't want to re-install, could you tell us what sort of network hardware your lappy is sporting?  If you arn't sure, post the terminal outputs of "lspci" and "lsmod" (also post "lsusb" if it's a USB wireless adapter)

---

### Post by cuboconojos on 2008-04-03
I would also suggest upgrading to 7.10. I had the same problem with WPA before, had to use wpa_supplicant... but with 7.10 everything works like a charm!

And just to make life easier... you shoul leave your router at home with open access, but using the MAC filter, allowing access to your laptop only.

Greettings from Chile!

---

### Post by drcdebaca on 2008-04-03
I totally agree with the above listed:  Reinstall.  It's the only thing that brought stability to my wlan ability on my laptop.   However, if you wanted to poke around a bit you could type lspci at the $ and see what wireless chipset you are working with.  It could also be a signal issue or a signal from a neighbor.  $iwlist wlan0 scanning will give you a list of signals, channel, and strength your wlan is picking up.  Best of luck.

---

### Post by ichi@YUKI on 2008-04-03
What's the deal with Ubuntu and wireless cards? How come everyone seems to be having trouble with wireless (including myself).. I think Ubuntu should work on that for it's next distros..

---

### Post by pseudo-random on 2008-04-03
> **ichi@YUKI said:**
> What's the deal with Ubuntu and wireless cards? How come everyone seems to be having trouble with wireless (including myself).. I think Ubuntu should work on that for it's next distros..
Agreed. They could do with making it easier but there is the factor of the knowledge of the user also.

---

