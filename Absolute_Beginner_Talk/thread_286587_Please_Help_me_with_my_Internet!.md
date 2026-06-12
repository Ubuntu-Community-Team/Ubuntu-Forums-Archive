---
title: "Please Help me with my Internet!"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by coolbian57 on 2006-10-27
I recently upgraded to Ubuntu 6.10.  I had my wireless internet connection working fine before upgrading to Ubuntu 6.10, although after updating I cannot seem to get it to work any longer.

I have a wireless USB adapter that works with Linux out of the box.  Linux perfectly recognizes the card and all I had to do was configure that connection.  I use a Hawking Wireless USB Adapter, and for anyone that is looking for such a tool, I highly recommend it.

However, I have configured (to the best of my knowledge) my connection that exact same way that I had it set previously on Ubuntu 6.06.  Yet it is still not working.  

The problem is that all of my parameters, including the Access Point and Essid, are deemed invalid.  I know this because I entered the command ```
Route wlan0
``` in the terminal.  

I currently have all encryption turned off, although it doesn't matter because I can't even get online.

I have manually changed the ESSID by enterting the code```
iwconfig wlan0 essid M*t**o*a*bde
```

...meaning that I changed my Essid to be correct.  However, after shutting down the system and restarting, the settings were not saved.

Can any Ubutu masters tell me what I should do to get Ubuntu to recognize my access point and ESSID name?

---

### Post by black_rob on 2006-10-28
Hi.  I'm not working at a Ubuntu machine right now, so I can't check for sure, but assuming your driver has been loaded (and it should be, because otherwise you wouldn't see "wlan0"), I would try "iwscan wlan0".  I've used that before and it's helped me find my access point, and then I change everything to match the access point.  Specifically, make sure the channel matches up, and that your card is in managed mode, then set ap to the the MAC address of your router, and set your essid to match the one given for the router.  That's usually worked for me.  Then either manually assign yourself an aaddress or use dhcpcd.  Or dhclient, I don't recall which one Ubuntu comes with.

---

### Post by black_rob on 2006-10-28
I meant "iwlist wlan0 scanning".

---

### Post by coolbian57 on 2006-10-28
> **black_rob said:**
> Hi.  I'm not working at a Ubuntu machine right now, so I can't check for sure, but assuming your driver has been loaded (and it should be, because otherwise you wouldn't see "wlan0"), I would try "iwscan wlan0".  I've used that before and it's helped me find my access point, and then I change everything to match the access point.  Specifically, make sure the channel matches up, and that your card is in managed mode, then set ap to the the MAC address of your router, and set your essid to match the one given for the router.  That's usually worked for me.  Then either manually assign yourself an aaddress or use dhcpcd.  Or dhclient, I don't recall which one Ubuntu comes with.

Okay i am going to try this.  Yes, i am using DHCP and it worked fine for me last time.  I don't know what you mean by setting the "ap" but I know what a MAC adress is and all that.  I know my essid, but I will use the one given by Linux instead.  That was probably the issue.

If anyone has some more hints on what to do, don't hesitate to post just because im gone :mrgreen:

---

### Post by coolbian57 on 2006-10-28
Okay I tried the iwlist commands and my wireless adapter is still not recognizing any access points...  Does anyone know how to fix this problem?

---

