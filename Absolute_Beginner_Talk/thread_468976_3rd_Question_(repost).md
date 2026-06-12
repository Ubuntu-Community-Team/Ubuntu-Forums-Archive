---
title: "3rd Question (repost)"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by MacScotland on 2007-06-09
3rd Question 

--------------------------------------------------------------------------------

Ok, with the very good help & advice from here I've now burnt a DVD with 7.04 on it and can boot live from it on my laptop. The basics seem to work, except internet connection.

I'm having trouble getting a connection to my wireless hub. It gets detected after I type in it's name, but it doesn't seem to accept the passphrase that I use with Vista. I've tried all combinations (I think) but to no avail. The hub documentation says to use 64 bit hex, and the passphrase is indeed a 10 digit hex string.

What could I be missing?

That said I'm making faster than expected progress 

I should add the documentation for the hub also says to use "open" rather than "shared" key.

--------------------------------------------------------------------------------

zero-9376  
5 Cups of Ubuntu
   Join Date: Sep 2006
Beans: 32 
 
Re: 3rd Question 

--------------------------------------------------------------------------------

Wireless is still a bit of a problem under ubuntu/linux have a search around the forums for your specific wireless card and see what comes up

--------------------------------------------------------------------------------

Ok, I've had a dig around and can verify I have a RALINK RT73 Wireless Card with supposed Linux support -

[http://www.ralinktech.com/ralink/Hom...ort/Linux.html](http://www.ralinktech.com/ralink/Hom...ort/Linux.html)
[http://www.ralinktech.com.tw/data/ReleaseNote](http://www.ralinktech.com.tw/data/ReleaseNote)

I've downloaded it and will give it a try with my live DVD version of 7.04. 

Question is now- what do I need to do to try it out? It's a .gz file, so will I need to decompress it first? If so, how? Where do I go to apply it while running off the Live DVD? Anything else to ensure I test this properly?


Anyone?
__________________

---

### Post by matthewboh on 2007-06-10
I've found that NetworkManager is working pretty well - but you have to comment out some lines in your /etc/network/interfaces file  Here's mine:

```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

And as long as you haven't used it during the current session, it seems like you can just go ahead and try it.  If you have used it, you would need to restart it - but the simplest thing is to just reboot.

And if you're using a WEP hex key, leave of the leading  0x

Hope that helps!

---

