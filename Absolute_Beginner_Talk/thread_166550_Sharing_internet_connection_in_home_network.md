---
title: "Sharing internet connection in home network?"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Blagomir on 2006-04-26
Can anyone help me with this? How can i share internet connection from my PC (UBUNTU) to my other PC (WINBOZE) ?

---

### Post by user1397 on 2006-04-26
Use samba! look it up in the forums there's tons of stuff on it

---

### Post by Nequeo on 2006-04-26
[QUOTE=erik1397]Use samba! look it up in the forums there's tons of stuff on it[/QUOTE]

Samba is for sharing files :) If you want to share an Internet connection, it's a bit trickier. We'll need to know more about how your Internet connection and network is set up. We also need to know if you're using Ubuntu 5.10 or 6.06 Beta. Connection sharing is very, very easy in 6.06. A little bit trickier under 5.10.

---

### Post by user1397 on 2006-04-26
[quote=Nequeo]Samba is for sharing files :) If you want to share an Internet connection, it's a bit trickier. We'll need to know more about how your Internet connection and network is set up. We also need to know if you're using Ubuntu 5.10 or 6.06 Beta. Connection sharing is very, very easy in 6.06. A little bit trickier under 5.10.[/quote]
Oops!

---

### Post by OffHand on 2006-04-26
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Use that if you have 2 networkcards on your Ubuntu machine and want to set it up as a gateway. Or buy a router  :)

---

### Post by Jason_25 on 2006-04-26
This is an instant 2-command process.

```

echo 1 > /proc/sys/net/ipv4/ip_forward

```
Will immediately begin forwarding IP's (routing).  Editing /etc/sysctl.conf you can turn it on permanently.

Since your internal IP's are probably not valid on the internet you will need to do IP masquerading too.  This is accomplished with IPTABLES.
```

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```
This will mask all your internal IP's with your external (valid) IP where eth0 is the name of your ethernet card.  Of course all PC's need to be on the same subnet.  Also, installing dnsmasq is stupid when you have that functionality built into iptables.  There is NO NEED to reboot when doing any of this.  Have fun.

---

### Post by SteveHoffmanUK on 2006-04-26
Blago

The short answer to your question is "with great difficulty". 

I tried it with the Ubuntu Breezy release and in the end gave up, went out and bought a wireless router/modem and solved the problem. The main difficulty was that I had what was called a "peer-to-peer" or "ad hoc" network, in which my computer was hooked into the Internet via an ADSL modem, with my wife's PC sharing my internet connection via a wireless netcard; both PCs run on XP Home. Onto this setup I tried to link my laptop running Ubuntu Breezy. Ubuntu isn't set up for ad hoc networks -- it is comfortable only with managed ones.

I expect it can be done, as you can do almost anything in Linux with enough savvy and effort, but I'm a newbie and, frankly just wanted to get my laptop online. It is now working beautifully, and I am a happy Ubuntu camper.

Good luck.

---

### Post by Nequeo on 2006-04-26
[QUOTE=Jason_25]This is an instant 2-command process.

```

echo 1 > /proc/sys/net/ipv4/ip_forward

```
Will immediately begin forwarding IP's (routing).  Editing /etc/sysctl.conf you can turn it on permanently.

Since your internal IP's are probably not valid on the internet you will need to do IP masquerading too.  This is accomplished with IPTABLES.
```

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```
This will mask all your internal IP's with your external (valid) IP where eth0 is the name of your ethernet card.  Of course all PC's need to be on the same subnet.  Also, installing dnsmasq is stupid when you have that functionality built into iptables.  There is NO NEED to reboot when doing any of this.  Have fun.[/QUOTE]

As a side note - this doesn't seem to work under Dapper 6.06. It's what I used in Breezy, and it worked brilliantly. But in Dapper, for one thing, there's no longer a /proc/sys/net/ipv4/ directory.

But I found a package called 'ipmasq' that sets up the iptable rules you need automatically. If you're using Dapper, just 'sudo apt-get install ipmasq' and away you go. Assuming you have the IP addresses on your cards set up right. It does have the unfortunate tendancy to occaisonally cut off my Ubuntu PC from the Internet (though the Windows PC still had access), but running 'sudo ipmasq' again whenether that happened fixed the issue

---

### Post by ukemike on 2006-04-27
Last weekend faced with the same problem and after learning that Ubuntu w/out an internet connection is... difficult, I went to compusa and was shocked at the price of routers.  I just wanted a garden variety non-wireless router and it was the same price as a 802.11g router.  BUT I found a 802.11b based wireless (with 4 hardwire ports) router for only $29.99.  Get a router it made the setup trivial (assuming you don't have dial-up)

---

### Post by Blagomir on 2006-04-28
Well, i installed firestarter and my internet connection is OK on my both (UBUNTU & WIN) machines.

But, how can i set the maximum traffic (KB/s) that my win can use?

---

