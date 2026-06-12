---
title: "Bittorrent Problems"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by bhavi on 2008-02-18
The bittorrent client in ubuntu gutsy getting stuck while downloading torrents

Error message is: The window(null) is not responding

TIA

Bhavani Shankar

---

### Post by julian67 on 2008-02-18
> **bhavi said:**
> The bittorrent client in ubuntu gutsy getting stuck while downloading torrents

Error message is: The window(null) is not responding

TIA

Bhavani Shankar
 
I'm no expert in this but maybe a couple of possibilities: problem with your bittorrent client (does it have pop up boxes/windows or need to give you notifications or messages from other clients?) or problem with one or more of the clients connected to your bittorrent client which might be sending bad packets.  Using p2p makes your PC highly visible, even behind a router,  and people/bots just hammer away at your open ports trying all kinds of stuff. If this a problem caused externally it's time to set up a firewall on the computer and check the logs of rejected packets. I use amule and transmission (another bt client) and the firewall log shows the open ports are bombarded with pings and other less friendly stuff. Some of this traffic (if allowed) can take down your client or even cause the kernel to need so much memory the whole computer slows down.  Also some ISPs (Comcast famously) deliberately inject erroneous packets in the legitimate traffic between the bt clients to kill the exchange. There are all sorts of nasty people out there and some of them we even pay :-(

---

### Post by bhavi on 2008-02-19
> **julian67 said:**
> I'm no expert in this but maybe a couple of possibilities: problem with your bittorrent client (does it have pop up boxes/windows or need to give you notifications or messages from other clients?) or problem with one or more of the clients connected to your bittorrent client which might be sending bad packets.  Using p2p makes your PC highly visible, even behind a router,  and people/bots just hammer away at your open ports trying all kinds of stuff. If this a problem caused externally it's time to set up a firewall on the computer and check the logs of rejected packets. I use amule and transmission (another bt client) and the firewall log shows the open ports are bombarded with pings and other less friendly stuff. Some of this traffic (if allowed) can take down your client or even cause the kernel to need so much memory the whole computer slows down.  Also some ISPs (Comcast famously) deliberately inject erroneous packets in the legitimate traffic between the bt clients to kill the exchange. There are all sorts of nasty people out there and some of them we even pay :-(
So.. Will Changing my bittorrent client work?

---

### Post by julian67 on 2008-02-19
> **bhavi said:**
> So.. Will Changing my bittorrent client work?

It might. Transmission is an excellent client and will be the default client in the next version of Ubuntu. It supports protocol encryption which the original bittorrent client doesn't. It's worth a try.

---

### Post by hyper_ch on 2008-02-19
or you could use rTorrent which is cli/ncurses based. Very lightweight yet very powerful.

Or kTorrent is a really great gui-driven client... azurueus is, as on windows, just a resource hog... you have also Deluge...

---

### Post by bhavi on 2008-02-19
Thanks guys will give it a try and report back

---

