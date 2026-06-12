---
title: "Suddenly Slow on Lenovo 3000 C200"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by timr92 on 2008-03-06
Hi, i'm *trying* to use Ubuntu 7.10 on this laptop. It has been working well most of the time that its been on there (2 weeks) but lately, and especially just before, it is really slow to start up. I thought it might have had something to do with its wireless thing and the router not turned on, but it wasn't. There was a NFS share meant to be mounting and it was unavailable so could that slow it down so it takes 5 minutes to start, rather than the 20 secs that it used to take, after the logon.

I have no desktop effects on, and uhm... I dont know if i can say anymore, LOL. Please ask me anything that may help sum1 help me with this problem.

Thanks in advance,
Tim

---

### Post by taurus on 2008-03-06
Are you trying to mount the nfs from /etc/fstab?  What happens if you edit /etc/fstab and place a # in front of the nfs entry to comment it out and see if that fixes the long booting delay?

---

### Post by timr92 on 2008-03-06
Yes, it was done with that fstab thingy. And i already deleted the line, but i haven't restarted it yet... Too scared, but i will shortly. I dont think that would be the problem though, as it was doing a little bit of this silly business before the shares were on there, and i think it has been booting when the share is not available.

---

### Post by Arthur Archnix on 2008-03-06
You can install a program called bootchart, which may help you identify exactly what is taking so long. Search for it in synaptic.

Once you've got your boot down to a reasonable level you can profile it which should help even further. You do that by adding profile to your kernel line just once, i.e., when booting go into grub menu list, instead of starting ubuntu highlight it and press 'e', then highlight the kernel line and press 'e', then add profile to the end of the line, then 'enter' and then 'b'.

Oh, and there's no need to delete the line from fstab. Putting a # in front like taurus mentioned is the functional equivalent.

---

### Post by timr92 on 2008-03-06
It booted fast that time, but if it wasn't that share, what could it be? Perhaps i could just wait and see if it does it again, and would the system logs help if it does it again, providing it still loads eventually. lol

---

### Post by timr92 on 2008-03-06
> **Arthur Archnix said:**
> You can install a program called bootchart, which may help you identify exactly what is taking so long. Search for it in synaptic.

Once you've got your boot down to a reasonable level you can profile it which should help even further. You do that by adding profile to your kernel line just once, i.e., when booting go into grub menu list, instead of starting ubuntu highlight it and press 'e', then highlight the kernel line and press 'e', then add profile to the end of the line, then 'enter' and then 'b'.

Oh, and there's no need to delete the line from fstab. Putting a # in front like taurus mentioned is the functional equivalent.

Ok... I just rebooted it and turned the wireless router off, and its slow again. Should i still do all that stuff that you said, or can we go on the fact that when the wireless router is off it goes slo. Thats going to suck when i go places away from home with it, taking 5 minutes to b ready...

---

### Post by Arthur Archnix on 2008-03-06
What's the output of 
cat /etc/network/interfaces

---

### Post by timr92 on 2008-03-06
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
        address 192.168.100.60
        netmask 255.255.255.0
        network 192.168.100.0
        broadcast 192.168.100.255
        gateway 192.168.100.1
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        # dns-* options are implemented by the resolvconf package, if installed
        dns-search ubuntu01
        wireless-key (NOT TELLING)
        wireless-essid OURHOUSE

iface eth1 inet static
address 192.168.100.61
netmask 255.255.255.0
gateway 192.168.100.1







































iface ppp0 inet ppp
provider ppp0

















































auto eth0

```

---

### Post by Arthur Archnix on 2008-03-06
Ok, that doesn't look too hot to me. Do you use network-manager?

Tell you what, if you do use network manager then try this:

Create a backup of you current file:
```
 sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```Then, open your current file:
```
 gksudo gedit /etc/network/interfaces
```And delete everything in there.

[I] Ctrl+A then Backspace or Delete

[/I] Then replace it with this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

If on the other hand, you like your current setup, then I'd suggest that way down at the bottom where you say auto eth0, you comment that out. You've got two auto's in there, lo and eth0. But me, I'd replace the whole thing with the default config, then use the network manager to connect.

---

### Post by timr92 on 2008-03-07
Well... I tried replacing the whole thing, but i needed to be able to put the gateway in, as the wireless router is just used as an access point, and the gateway is another router. Also, was it trying to use DHCP, that doesn't suit me either. So i restored it, and commented out eth1, becuase i wanted to use the wireless, but then it has put it back, uncommented, at the end there. Oh, and what is network-manager, if it is what happens when you go System > Administration > Network, or go to manual config in that network icon in the panel, then yes i use it.

So, uhm... I like that roaming stuff, but can i set the gateway and IP address with that?

---

### Post by timr92 on 2008-03-07
Help.. Please.. Sum1. Is there another way to manage the networking stuff that wont slow it up if something is unavailable, or can i disable the wired network?

---

### Post by timr92 on 2008-05-03
I managed to fix the prob by using Wicd, and making sure it didn't "Automatically reconnect on connection loss"

---

