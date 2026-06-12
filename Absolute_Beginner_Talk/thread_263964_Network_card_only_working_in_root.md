---
title: "Network card only working in root"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by JimmyLightning on 2006-09-24
Hi, I just installed Ubuntu 6.06 but forgot to plug in my network cord until after I'd finished the installation. So, it's not showing up at all in my network list. I did some googling and found something about the " lspci -v " command on these forums, so I did that command and "Communication controller" shows up but at the bottom it says "Capabilities: <available only to root>".

I should also point out that I've run the Live CD on this computer several times and it's always found the network card before, so I know it can.

So, I guess my question is, do I have to log into root to change something so that I can have access to the internet, and if so, what do I need to do? Or is there another way to get it to work?

Thanks in advance!

-Jimmy

---

### Post by b_martinez on 2006-09-24
Is this an ethernet card? If so try opening a terminal and typing in 

sudo ifdown eth0  

then enter your user password when asked. You will not see anything show on screen, but hit 'enter' when it is typed out.
 Now type in 

sudo ifup eth0

hit 'enter' key and type in 

sudo dhcpcd

again hit enter key. If you get a "command not found" or similar message, type in 

sudo dhclient eth0

Hope this works for you
Bill

---

### Post by bodhi.zazen on 2006-09-24
In a terminal open an editor:
```
sudo gedit /etc/network/interfaces
```

Add these lines:> # The primary network interface
auto eth0
iface eth0 inet dhcp

Save and exit.

Now in a terminal:```
sudo ifup eth0
```

should be good to go. (network will come up automatically on re-boot as well).

---

### Post by JimmyLightning on 2006-09-24
Thanks for the reply, Bill. 

Yes, it's an ethernet card, sorry for not saying that. After the first command (sudo ifdown eth0 and my password), it said "ifdown: interface not configured". 

The last command brought up a bunch of "device not found" errors. 

Does that first one mean I need to configure my ethernet card? And if so, how do I do that?

Thanks.

Jimmy

---

### Post by JimmyLightning on 2006-09-24
Thanks for the reply, I did that and those two lines were already there. Then when I did sudo ifup eth0, it came up with several "device not found" errors. 

First line: "SIOCSIFADDR: no such device"
Second line: "eth0: error while getting interface flags: No such device"
Third line: "eth0: error while getting interface flags: No such device"
Fourth line: "Bind socket to interface: no such device"
Fifth line: "Failed to bring up eth0."

Thanks for your help.

Jimmy

---

### Post by bodhi.zazen on 2006-09-24
First the obvious, are you sure the card is installed properly?

If so, what card is it exactly?

---

### Post by JimmyLightning on 2006-09-24
I'm pretty sure it's installed right since I've used the Ubuntu 6.06 Live CD several times on this machine before installing it and it's worked fine, and there's a little green light on the card that's on. So I'm pretty sure it's installed. 

Um, I'm not sure what type of card it is. It's about 5 years old, I know that....I can try to dig up more info on it....

Thanks. 

Jimmy

---

### Post by LookTJ on 2006-09-24
try the eth1 instead of eth0

---

### Post by jordanmthomas on 2006-09-24
Or, just post the results of
```
ifconfig
```

---

### Post by JimmyLightning on 2006-09-24
Hmm, I'm getting the same errors. 

The first error I'm getting is that it's not configured, how would I go about configuring it?

Thanks.

Jimmy

---

### Post by JimmyLightning on 2006-09-24
"eth0: error fetching interface information: Device not found"

Same with eth1.

Jimmy

---

### Post by JimmyLightning on 2006-09-24
I'm pretty sure the Live CD has the correct driver(s) on it (since I've gotten internet before on the computer using it), they just didn't install because my network cord wasn't plugged in while I was installing. Is there some way I can get the driver(s) I need off the Live CD?

---

### Post by bodhi.zazen on 2006-09-24
Boot to the live CD.

to list loaded modules:```
lsmod
```
find the module for your ethernet card.

Now,boot to HD
```
sudo modprobe <module name>
ifup eth0
```

If that works, add the module to /etc/modules.

---

### Post by JimmyLightning on 2006-09-24
Oh, sweet. I'll try that later today when I have time.

Thanks.

---

### Post by JimmyLightning on 2006-09-24
P.S. how will I add it to /etc/modules? I've never worked with that before, so I'm not sure if I'll be able to see what to do or not.

Is /etc/modules a folder? If so, will I just save in my module? And how do I do that from the terminal (which is where I'll be, if I'm reading this correctly?)

Thanks so much, this sounds like it'll solve my problem!

Jimmy

---

### Post by bodhi.zazen on 2006-09-24
> **JimmyLightning said:**
> P.S. how will I add it to /etc/modules? I've never worked with that before, so I'm not sure if I'll be able to see what to do or not.

Is /etc/modules a folder? If so, will I just save in my module? And how do I do that from the terminal (which is where I'll be, if I'm reading this correctly?)

Thanks so much, this sounds like it'll solve my problem!

Jimmy

```
sudo gedit /etc/modules
```

Add the module at the end of the file, on it's own line. Save and exit.

---

### Post by crokett on 2006-09-24
Link to an example /etc/modules file

[http://astro.berkeley.edu/~mperrin/software/modules](http://astro.berkeley.edu/~mperrin/software/modules)

I'd also do a google search on /etc/modules to find out what it is and what it does.

to edit it:
(back it up first) 
```
sudo cp /etc/modules/etc/modules.bak 
```
now open for editing:
```
sudo gedit /etc/modules/etc/modules.bak 
```

---

### Post by JimmyLightning on 2006-09-25
OK, I got more information. Oddly, it's now not working with my Live Ubuntu CD, either. But it is working for my Windows ME installation, so I got the information on it while I was in Windows: it's a "NETGEAR FA310TX Fast Ethernet Adapter".

Should I do a google search for a module for that? And if so, how will I get the module into my Ubuntu?

Thanks for helping me through this, everyone. :)

Jimmy

---

### Post by dmizer on 2006-09-26
JimmyLightning, this is something more basic than a driver ... i'm sure of it.

i know i have the right driver for my card.
i also know that eth0 is the correct designation for my card:

```
[17179702.056000] pcmcia: registering new device pcmcia0.0
[17179703.112000] eth0: Asix AX88190: io 0x300, irq 3, hw_addr 00:00:00:00:00:00
```
heres my cardctl ident:
```
$cardctl ident
Socket 0:
  product info: "Network Everywhere", "Fast Ethernet 10/100 PC Card", "3.0", "AX88190"
  manfid: 0x0149, 0xc1ab
  function: 6 (network)
```
my interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet dhcp
        wireless-mode managed
        wireless-essid myessid

auto eth0
iface eth0 inet dhcp
```
but if i try to activate the card:
```
$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
```

i also know for sure that the correct module is loading for this card because the correct module appears in lsmod:
```
$ lsmod | grep pcmcia
pcmcia                 40508  1 axnet_cs
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
```
i'm absolutely positive axnet_cs is the correct module for my card.

so the problem is that despite the fact that dmesg assigns eth0 to the card, and the card is installed properly, and configured correctly in interfaces, and the correct module is assigned to it ... ubuntu still does not know the card exists.  previously, i would fix this issue by making eth0=eth0 entry in /etc/network/run/ifstate, but that's no longer a part of dapper.

furthermore, i know that this card will work if it i would have the ability to configure it with network manager in gnome, because it works for everyone else that way.

it also works on my other ubuntu machine where i installed with this card atached.

---

### Post by JimmyLightning on 2006-09-26
> JimmyLightning, this is something more basic than a driver ... i'm sure of it.

You, umm, seem to be right. I just booted up and it works suddenly. No idea why! :o 

Thanks for all the help.

Jimmy

---

### Post by dmizer on 2006-09-26
> **JimmyLightning said:**
> You, umm, seem to be right. I just booted up and it works suddenly. No idea why! :o 

Thanks for all the help.

Jimmy

lol ... i wish mine would be so easy.  i've been trying to make this stupid thing work for weeks.  ah well ... motor on.

---

