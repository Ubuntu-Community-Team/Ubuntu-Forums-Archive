---
title: "Port Forwarding PPC using ubuntu"
date: 2007-07-27
forum: Apple PPC Users
---

### Post by Sanchoclaus on 2007-07-27
Could anybody please help me?
I'm using ubuntu 7.04 on a an emac G4 Macintosh
My modem is a LINKSYS  WRT54G  Wireless G Broadband router (ethernet)
I've search all over the internet and can't even seem to configure a static ip address. Every time I think I get it right, the internet doesn't work at all.
Any help would be greatly appreciated!

---

### Post by Ek0nomik on 2007-07-27
You don't *have* to have a static IP address to get port forwarding to work.

You should just need to log into your router and navigate to the port forwarding screen.

You will need to know your internal IP address however.

```
ifconfig
```

will list your internal address.

Once you know the last set of digits, you can plug them into your port forwarding section of your router management.

---

### Post by Sanchoclaus on 2007-07-27
Thank for your suggestion. I used that same command "ipconfig" on my toshiba laptop and got it, but on my mac when typing that command in it says "command no found. Are there any alternative commands to get the ip info?
Thank you

---

### Post by Ek0nomik on 2007-07-27
> **Sanchoclaus said:**
> Thank for your suggestion. I used that same command "ipconfig" on my toshiba laptop and got it, but on my mac when typing that command in it says "command no found. Are there any alternative commands to get the ip info?
Thank you

I posted 'i**f**config', *not* 'i**p**config'.  :)

'ifconfig' will work on your Ubuntu system.

---

### Post by Sanchoclaus on 2007-07-28
Thank you Ekonomic! I got the port on my router set. And got my statit IP up and running, even though you said it wasn't  necessary. The "ifconfig was very helpful

---

### Post by Sanchoclaus on 2007-07-28
If its any help to people with my problem running Ktorrrent, this is how I configured my router.
[Www.portforward.com](Www.portforward.com) doesn't have a guide routing Ktorrent, so what I did was use the instructions from the Azureus torrent client.
Once you tipe in the router address on your modems page and get to the firewall part.
Try these ports:
 TCP: 6881
UDP tracker port: 44444

I hope my experience is helpful

---

