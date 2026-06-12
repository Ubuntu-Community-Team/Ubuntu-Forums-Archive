---
title: "Oldworld Wallstreet, Xubuntu 6.06, and stuck."
date: 2008-12-14
forum: Apple Hardware Users
---

### Post by OpEdMunkey on 2008-12-14
Successfully installed Xubuntu 6.06 command line. Appears to be successful. Man pages don't work. I'm stuck on installing X and the rest of the GUI.

Anyone know how to configure a network connection at the command line?

---

### Post by pxwpxw on 2008-12-14
> **OpEdMunkey said:**
> Successfully installed Xubuntu 6.06 command line. Appears to be successful. Man pages don't work. I'm stuck on installing X and the rest of the GUI.

What have you tried?
> 
Anyone know how to configure a network connection at the command line?
Wired or wireless?

That might get more anwers.

---

### Post by eraker on 2008-12-15
What do you get from the command ifconfig?

If you get eth0 and lo ouput, then you should check /etc/network/interfaces next.

Can you ping your router? try ```
ping -c3 192.168.1.1
``` (which is used by a lot, but not all, of routers).

With a simple modem/router dhcp setup that your computer is wired to, it should be something simple. The following is exactly what my current /etc/network/interfaces file reads:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```


If you have nothing in /etc/network/interfaces or if it's entirely commented out (with #'s) then (assuming you're using a wired connection) you can try to edit it to read what's above. 

Then, I'd try manually stopping and restarting networking: 
```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start.
```

These are the same commands the system runs for networking when it boots. Sometimes there's useful info in there. 

Then, you can try to ping somewhere beyond the router: ```
ping -c3 www.google.com
```

I use this command so much on my iBook Clamshell that I have a bash alias for it.

Finally, if you can ping google (you're sending and receiving), and you're having trouble installing packages, I'd check your apt repositories:
```
cat /etc/apt/sources
```

All of these tricks are based on the most standard set-ups: modem/router/ wired-ethernet, with a real basic install. Things could be different for you, but these are the things I usually try.

---

### Post by OpEdMunkey on 2008-12-17
Thanks to folks who have responded.

interface file contains:
auto lo
iface lo inet loopback

auto et0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


ifconfig command returns:

lo	Link encap:Local Loopback
	inet addr:127.0.0.1 Mask:255.0.0.0
	UP LOOPBACK RUNNING MTU:16436  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX same as abover ends with carrier:0
	collisions:0 txqueuelen:0
	RX bytes:0 (0.0 b) TX bytes:) (0.0 b)


I'm assuming I have to configure an interface but I'm not sure if one users ifconfig to do that. Off to do some additional R&R as well as try the stop/start network - just in case.

---

### Post by OpEdMunkey on 2008-12-17
This thing acts like it cannot see the NIC. Is there a command that will  return whether the OS sees a network interface? Things did work when the Apple OS is installed. Could it be a driver issue?

---

### Post by OpEdMunkey on 2008-12-17
lspci does not return an Ethernet controller. That can't be good.
With a wireless card in lspci does return the presence of the Broadcom wireless chipset.

---

### Post by eraker on 2008-12-18
I think the Broadcom chipset might one of the ones that has problems. I could be wrong, but it seems to be ringing a bell (I have Orinoco and it also has problems; it can do WEP and straight wi-fi but not WPA). 

If you're not getting output from lspci then that's the place to start. The hardware itself might not work or the kernel modules might be wrong or not even loaded (these are just guesses).

If you enter the command "lsmod" it will show you all the modules loading and you should see what's loading to talk to your ethernet/wired and wireless cards.

It might be worth it to do some googling also on that chipset and see if you can find if other people have had similar issues.

---

### Post by OpEdMunkey on 2008-12-18
The Broadcom chipset most definitely has problems. I have configured one in the past and it's definitely a good time.

That's why I decided to work on the wired connection first. Imagine my surprise. The hardware does work with the Apple OS installed. It was not connected to a network during the install. I'll try lsmod and see what I get.

---

