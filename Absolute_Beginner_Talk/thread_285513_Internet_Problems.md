---
title: "Internet Problems"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2006-10-26
Alright, so I'm having problems with my internet connection. I've had Dapper installed on a computer for a while now, since probably June. However, I haven't been using that computer very much, I'm in the [very long] process of switching over to it. The internet worked fine, but one day, it just STOPPED working. I didn't change anything, it just stopped. After a long time and a lot of settings changes, it started working again, but the network monitor or whatever still said it couldn't connect.

So today I upgraded to Edgy, hoping my problem would be solved. Needless to say, it wasn't. I use static IPs on my home network, I've set that up on the computer; still, no dice. The connections properties show that it's connected with eth0, and says the connection is idle (221 packets sent, 48 received). Any ideas as to how to fix this? I just have no clue.

---

### Post by magicfab on 2006-10-26
Faulty cable ? Have you tried DHCP, just to make sure the cabling is OK ?

You could also use statically assigned addresses with MAC address filtering instead of static addresses.

---

### Post by chimerical_brio on 2006-10-26
Alright, thanks a lot, that worked.

I do have one question though: using DHCP, will I be able to use BitTorrent to fast speeds? That's why I had static IPs set up, and I'd like to not have snail-crawl speeds.

---

### Post by magicfab on 2006-10-27
You can use DHCP and have the router assign always the same address. What router do you have ? Check the documentation for "static DHCP assignment" or similar.

Once you have done that, specify port to open for bittorrent on that IP address.

---

### Post by Henry Rayker on 2006-10-27
I use DHCP with MAC address filtering, and I get great speeds on my bittorrent.

---

### Post by chimerical_brio on 2006-10-27
Alright, so with DHCP on, things have been working fine. But now I have a new problem: on the panel in GNOME, I placed a network connection monitor, and it shows my connection as being fine. However, another one has just randomly shown up, I can't remove it from the panel, and it keeps telling me that the connection is broken. The connection is not broken. I am fully able to get online. Any ideas?

---

