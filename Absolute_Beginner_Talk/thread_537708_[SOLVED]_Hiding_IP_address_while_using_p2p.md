---
title: "[SOLVED] Hiding IP address while using p2p"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2007-08-29
Does anyone know if there are any programs that allow anonymous p2p i.e. stop people from seeing my IP address while I am using p2p. In Windows, I used PeerGardian for this.

Specifically I use the BitTorrent network. In Ubuntu, I've been using KTorrent, although I can change to some other client if this would enable privacy.

So, does anyone know of any programs that can hide my IP address while using p2p? Or alternatively, does anyone know of any bit torrent clients that an hide my IP address?

Thankyou.

---

### Post by boogieboarder97 on 2007-08-29
you can try privoxy heres the setup guide [https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

---

### Post by Hallvor on 2007-08-29
> **NovaAesa said:**
> Does anyone know if there are any programs that allow anonymous p2p i.e. stop people from seeing my IP address while I am using p2p. In Windows, I used PeerGardian for this.

Specifically I use the BitTorrent network. In Ubuntu, I've been using KTorrent, although I can change to some other client if this would enable privacy.

So, does anyone know of any programs that can hide my IP address while using p2p? Or alternatively, does anyone know of any bit torrent clients that an hide my IP address?

Thankyou.

Why don`t you use the IPfilter plugin in kTorrent and load the lastest ipfilter? Ipfilter won`t make your IP invisible - it will just block *known* snoopers and evildoers. Some people have received letters from the **AA even when using ipfilter.

---

### Post by OoooMatron on 2007-08-29
peerguardian only blocks ip ranges on the internet which means you cannot download from people you are blocking. there are programs that use the same block lists as peerguardian and you can use those in other firewall software.

---

### Post by NovaAesa on 2007-08-29
> **Hallvor said:**
> Why don`t you use the IPfilter plugin in kTorrent and load the lastest ipfilter?

How do I do this (load the latest filter I mean)?
Sorry, I'm a Linux/Ubuntu noob.

---

### Post by bogolisk on 2007-08-29
Sorry but PeerGuardian (or ktorrent's IPFilter) doesn't hide your IP. It's completely useless for hiding from the **AA  because your IP is broadcasted by the tracker. They don't need to connect to you to know what are you sharing. TOR (which requires tracker support, AFAIK) will *try* to obfuscate your traces but don't worry they will find you as well if they want.

If you're paranoid then don't p2p!

---

### Post by st33med on 2007-08-29
Ipmasq does a very good job
```
sudo apt-get install ipmasq
```

---

### Post by -SpaZ on 2007-08-29
You can't hide your IP address, but you could use a proxy.

---

### Post by st33med on 2007-08-29
> **-SpaZ said:**
> You can't hide your IP address, but you could use a proxy.

Yes, that's what proxies do. They hide the IP address of the computer and display the proxies IP.

---

### Post by -SpaZ on 2007-08-29
> **st33med said:**
> Yes, that's what proxies do. They hide the IP address of the computer and display the proxies IP.

You can never truely hide your IP address, you can just make it harder to find.  You're still giving your IP address to the proxy.

---

### Post by Hallvor on 2007-08-30
> **NovaAesa said:**
> How do I do this (load the latest filter I mean)?
Sorry, I'm a Linux/Ubuntu noob.

Don`t have kTorrent in front of me, but look through the menus and look for "plugins". There you`ll find a IPfilter plugin. Select it, restart kTorrent and look for IPfilter in the menu. You`ll have to download the ipfilter to make it work.

---

### Post by phyrewall on 2007-08-30
I would run TOR w/ Vidalia (noob proofs TOR), ipMasq, and IPblock.

Again, it's really hard to be completely "invisible" on the net, but these systems make it harder to figure out who you are. 

Of course, the more you have in between you and the P2P network, the slower your speeds are going to be.

Oh, and try to only use private trackers.

---

### Post by NovaAesa on 2007-08-31
Thanks everyone! I can't get to my computer right now (I'm at my girlfriend's place for the weekend), but I'll see if I can get it all working on Monday night.

Vidalia looks really good from looking at their website, so I'll be sure to give that a try. I'll give the other options a go too.

Thanx!

---

### Post by bone2006 on 2007-09-01
Maybe it's just me, but a true proxy isn't going to work.  You can hide your IP if your going to browse the internet using a proxy, but trying to use a proxy to download say a GB of data will get you kicked off and banned from the proxy, even if you could it's going to be slower than anything.
This isn't something that's ubuntu related, because if there was something that easy everybody on a computer would do it regardless of platform.

If data is leaving your computer your IP is going to be recieved by the other end, unless you go through a proxy, which would mask your IP and use their IP, which is going to use their bandwidth.  Therefore the only methods I can see you using is maybe the Ktorrent posts about using their filter so that you can't connect to one of the known spyers's IP, so you would be protected from connecting to their IP, yet that's not blocking your IP.

If your just going to browser the internet then a proxy would work out just fine for you, but downloading at fast speed and a lot of data, I don't see it happening and if so let me in on the secret that half the people I know would love to know.

---

### Post by zerobinary on 2007-09-01
Wouldn't proxy slow u down a lot .

---

### Post by -SpaZ on 2007-09-01
> **zerobinary said:**
> Wouldn't proxy slow u down a lot .

Not if you use a good proxy.

---

### Post by bone2006 on 2007-09-01
> Not if you use a good proxy.

Where would one find this excellent proxy?  Seems to me if anything is that excellent that more people would use it, thus slowing down the speeds.  Unless you are breaking into another computer or using another computer and you are the only one using their connection as the proxy.
  
If there is such a good proxy out there that's offered to the public why not just post it?  Unless it's a cousin's aunt's sister computer who lives in sweden that is being used as the good proxy.

I've used so many proxies to visit websites with decent speeds, I've never used a public proxy that I could download even a 1/8 of my current speed and even the attempt generally will get you banned for killing their bandwidth.

---

### Post by Hallvor on 2007-09-01
You can get a certain amount of anonymity, but the overhead cost is staggering and the files are few. I believe you must be looking for something like this. Trying to run heavy bittorrent traffic through a proxychain... well, good luck with that!

[http://mute-net.sourceforge.net/](http://mute-net.sourceforge.net/)

---

### Post by NovaAesa on 2007-09-04
Thanks everyone for helping. I think I'll just stick with IP filter, as that was the only level of (equivalent) protection that I was using with Windows. The whole proxy thing seems to be a no-go as I don't really want to be clogging up people's band width.

Thankyou

---

