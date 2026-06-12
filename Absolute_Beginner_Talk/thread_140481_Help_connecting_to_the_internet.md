---
title: "Help connecting to the internet"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by Koi_Boy on 2006-03-06
Hey gang-

Total Linux noob here trying to get connected. I have just installed 5.10 and after I fiugured out how to get my Nvidia card working I am now stcuk trying to get on the internet.

I think I have everything setup right as I can ping my router yet I cant ping anyhing beyond it so I feel there is some issue on how my router is passing off to my machine.

I have setup a static IP as I could not figure out how to get DHCP to work.

ifconfig seems to report all is well as it shows the ip numbers I would expect and no errors.

Anybody know how I move on from here?

Using a Linksys router connected to a cable modem.

Regards,

Dwayne

---

### Post by halfvolle melk on 2006-03-06
Hi,
What output do you get from this?:
```
cat /etc/network/interfaces
```

---

### Post by Koi_Boy on 2006-03-06
Thanks for your quick reply

other than comments (I cant copy and pate yet as the Linux box is not on my network yet)

auto lo
iface lo inet loopback

mapping hotplug
              script grep
              map eth0

iface eth0 inet static
address 192.168.1.120
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

iface dsl-provider inet ppp
provider dsl-provider

---

### Post by halfvolle melk on 2006-03-06
Well, that seems to be ok if your router is indeed 192.168.1.1. I'v got a fixed DNS in there as well, but you wouldn't need that for pinging. Maybe router<-->modem is the problem.

---

### Post by LordBug on 2006-03-06
Pinging the router means the basics are good.  Are you trying to ping by name or by IP address?  If by IP works and by name doesn't, then you have a DNS problem.  If neither work, you likely have a Gateway problem.

---

### Post by Koi_Boy on 2006-03-06
Yeah, thats what has me puzzled as I do have two Windows boxes hooked to the same router and they communicate with the net just fine as you can tell from this post ;-)

Regards,

Dwayne

---

### Post by LordBug on 2006-03-06
Check what the Windows boxes have for Gateway and DNS settings (ipconfig /all).  Mirror the Linux system to match.

Did you check pinging by IP address vs. by name yet?

---

### Post by Koi_Boy on 2006-03-06
welllll, I don know what I saw earlier but I just tried pinging my router again at 192.168.1.1 and am getting no response.

The cable is good as lights are on on the ethernet card and I swapped the cable and port from a working Windows connection.

Could the network card not be configured proprly or drivers?

Dang I hate setting up new boxes.

Regards,

Dwayne

---

### Post by halfvolle melk on 2006-03-06
Try:
```
sudo /etc/init.d/networking restart
```
It might have stopped for some reason.

---

