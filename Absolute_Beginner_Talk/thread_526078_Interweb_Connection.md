---
title: "Interweb Connection"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Lord Rocket on 2007-08-15
Hello,

I received my Ubuntu LiveCD in the post the other day and after some hassles (you REALLY shouldn't say that the LiveCD only requires 256 meg of RAM, since it obviously needs more than that to install it) I managed to get the thing up and running.

Griping aside, I'm very satisfied with what's come 'out of the box'. Quick, everything I could desire comes pre-installed, and nicer looking than XP if I do say so myself. However, I am keen to put a few games, and the 'restricted content package' on there, so I won't have to boot up Windows every time I feel the need to put off doing anything university-related (which is often).

Unfortunately, after I dragged my computer over to Dad's, so I could use his speedy, wired ethernet broadband connection (as opposed to my remarkably slow non-existent connection), I began to have further problems. The interweb seemed to connect after filling in the IP and DNS sections in the Properties tab of the Network 'wizard', but good luck opening a webpage or apt-getting anything. I double checked the relevant numbers and tried a DHCP connection, but, again, nothing.
'sudo pppoeconf' got no further than the first couple of attempts to connect when I tried that, and informed me that perhaps something else was hogging the connection, or that I should check the wires. 
I did that, and removed all the details from the Network utility, but got the exact same result - which is to say, nothing.

Fearing some sort of hardware incompatibility, I booted XP and set up the web connection there. When I cleared up a couple of typos it all worked just fine. I returned to Ubuntu hoping vaguely for a miracle cure, or at least the ability to notice something I'd missed, but... same problem.

So... what's going on? I followed the instructions in the help file as exactly as I could, and no other documentation I've looked at has suggested any alternate path to connecting than the one laid out therein. 

If it helps at all, I'm using the inbuilt ethernet connection in my motherboard, the ASUS A8V-MX ([more specs here](http://www.dealtime.com/xPF-ASUS-Asus-A8V-MX-AMD-Skt939-VIA-K8M800-PCI-E-AGP-DDR400-SATA-RAID-LAN-6ch-audio-USB2-up-to-DDR400-mi)).

By the way, I'm both a Ubuntu n00b and an English major. I appreciate any help you care to give, of course, but you'll have to deliver it very simply for me, and with plenty of redundant information.

Thanks in advance.

---

### Post by uzerzero on 2007-08-15
Do the lights on your computer show up, to indicate that there is a link? These will typically be green LEDs near your network jack. If not, then Ubuntu is not even loading your network drivers. If they are lighting up, then at least Ubuntu has some drivers loaded. As for connecting via the network, ask your dad for the settings on his router and if you can connect it to via static IP. Static, as opposed to DHCP, is an IP address that you specify. Odds are, your IP address will be something like 192.168.0.3, the Subnet Mask as 255.255.255.0 and the Gateway Address as 192.168.0.1. Using Static IP, you should be able to get yourself a connection.

---

### Post by splintercellguy on 2007-08-15
Please post the output of ifconfig and lspci in Terminal in Ubuntu.

---

