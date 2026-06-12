---
title: "Need with with re-routing traffic"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by electripfy on 2008-01-16
Thanks for reading this thread, I hope I can provide enough information for someone to help me with this. I'm new to Ubuntu, and Linux in general, but not a complete idiot in most matters related to computers.

The problem is relatively simple. There has been much talk in the World of Warcraft community that it is possible to drastically lower ping to the game server by adjusting traffic behavior. It appears that packets are being held up unnecessarily and it is suggested that this be done to lower game ping:

Install Linux (via VMWare or just on another box) and run the following commands having installed the necessary packages. After that simply route your traffic through Linux/VMWare.

**sudo iptables -t nat -A PREROUTING -p tcp -d <WOW SERVER IP> --dport 3724 -j REDIRECT --to-ports 3724 press**

**sudo socat -d -d -d TCP4-LISTEN:3724,nodelay,fork,reuseaddr,su=nobody TCP4:<WOW SERVER IP>:3724,nodelay**

It is easy to re-route traffic with things like FreeCap (or simply using the 'route' command) etc on Windows. And that is also slightly different from my problem, since I don't run Linux on a separate box or virtual machine

Any assistance in accomplishing the same thing on Linux is much appreciated.

PS. I run WoW in Linux using Wine.

---

### Post by hyper_ch on 2008-01-16
> 
Install Linux (via VMWare or just on another box) and run the following commands having installed the necessary packages. After that simply route your traffic through Linux/VMWare.

Note: linux box refers to either a linux box or virtual linux install


If I'm reading this right, they tell you to

(1) setup a linux box on your network
(2) add those commands to your linux box (or rather to iptables)
(3) have all traffic routed through that linux box

I guess they recommend to setup that linux box so that you just can add those rules to iptables because it is much simpler to do on a real firewall than on windows. If that is the case, then just run those commands on the box your playing in wine. That should do the trick.

but then, I'm no expert on that. It's just what my impression is.

---

