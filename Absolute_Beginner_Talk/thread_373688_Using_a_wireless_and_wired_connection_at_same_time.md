---
title: "Using a wireless and wired connection at same time"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Kossu on 2007-03-01
Hello,

I got 2 ISPs, both come thru with cable, however one is connected to a router. They both work fine, separately. However I don't seem to be able to connect to both wireless and wired at same time, and whenever changing the connection type im forced to restart, is it really necessary?

Do anyone have a clue on how to get both to get an local ip and working? (both use DHCP)

Thank you very much in advance.

---

### Post by Spin Doctor on 2007-03-01
I dont think you could use both connections at same time.

If you use networkmanager it is easy to shift your internet connection without have to restart.

---

### Post by luke411 on 2007-03-01
My guess is that this is more of a wireless card issue than anything else. It has only been recently that we've has the luxury of complaining about the annoying aspect of wireless cards in Linux, as it used to be the best part of a week to get them to work at all.

I can only tell you what I have done on my home network, though I don't try to use two connections at once. I ended up using fixed IP addresses for all of my computers because for some reason, my wireless card would have difficulty in getting a new IP address from my router at each boot and would often try to use the same one. For some reason this is my router specific because it works fine on the road, using DHCP in hotels or what not.

Still, with a fixed IP address I have to occasionally enter into the network settings and manually force it to reconfigure the network device in order to connect. Otherwise I get a connection signal but can't actually do anything on the net.

I hope all of this helps. I guess my advice is to play with your settings and find something you can live with. I could always go buy a usb NIC and try using a different driver but what I do works for me, and I can live with it.

---

### Post by Kossu on 2007-03-02
Hello

Thanks for the replies. 


I'm still confident that there must be a way, if you think about it, Linux is a reliable server OS. And for it to not be capable of handeling 2 independent connections at the same time would be insane.

I've poked around a bit, and so far ive noticted that the network manager has DNS as a general option (meaning that you _can't _edit the DNS _independently_ for each connection easily) Which is a requirement when using 2 connections. 


@2nd reply: Luckily im blessed with a linux supported wlan card, and its been working wonderfully. Just not together with another connection :(


Thanks for the replies once again.

---

