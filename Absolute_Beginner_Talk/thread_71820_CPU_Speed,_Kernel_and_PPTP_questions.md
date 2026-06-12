---
title: "CPU Speed, Kernel and PPTP questions"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by loupy on 2005-10-04
I am somewhat new to linux - I tried Redhat and SuSe a couple of years back and found them very difficult to work with.  Ubuntu has been working quite well for me and I am hoping that after the full release of Breezy I'll be Window$ free.

On to my questions :) :

1. With powernowd enabled my CPU is set at 802Mhz.  I am not sure if it steps up when processing occurs, but I was wondering if there was a way to have it run at 2.2Ghz while plugged in and step down when I am on battery?

2. I am running Ubuntu on a Gateway 7422GX, AMD 64 Mobile Athlon 3400+ 1GB ram 64MB ATI Radeon 9600 (I think it is just a repackaged 9550) - I know that there are issues with the 64bit distro (especially with Java, Ndiswrapper, etc) but I like tinkering around so I don't mind that - However I do not know which is the right kernel to use for my machine.  There is an AMD64-Generic, K7, but no K8 for Breezy, will Tamir's K8 for Hoary work on Breezy? is my machine even K8 compatible?

3. I cannot get pptp to work at all.  I've tried using Kvpnc (even though I am on gnome) and it connects but even with it set to tunnel all traffic I cannot see any servers on the otherside.

Thank you for taking the time to read this.

---

### Post by cwaldbieser on 2005-10-04
[QUOTE=loupy]
3. I cannot get pptp to work at all.  I've tried using Kvpnc (even though I am on gnome) and it connects but even with it set to tunnel all traffic I cannot see any servers on the otherside.
Thank you for taking the time to read this.[/QUOTE]
I take it you are trying to esablish a Cisco VPN connection?  I have never used kvpnc, but I have used vpnc from the command line.  Once you connect, open a terminal and type:
```

$ ifconfig

```
Do you see a device called "tun0" or something similar?  If so, try looking at your routing table:
```

$ route

```
You might just need to set up a route to send packets to the tunnel if they are destined for the remote network.

---

### Post by Ampersand on 2005-10-04
[QUOTE=loupy]
1. With powernowd enabled my CPU is set at 802Mhz.  I am not sure if it steps up when processing occurs, but I was wondering if there was a way to have it run at 2.2Ghz while plugged in and step down when I am on battery?[/QUOTE]

It does step up. That confused me for a while when I first found a cpu frequency monitor. (: I've tried setting the frequency using cpu-freq (available from synaptic), but it seems to still set itself automatically. You can use it to set the maximum speed, though.

---

### Post by loupy on 2005-10-04
I do not need a cisco VPN config or IPSEC.  I only need a pptp connection with MPPE (so I learned after 2 days of searching).  I have been unable to find a vpnc.conf example that would allow me to do this.  Anyone have one they can provide me?

Unfortunately I cannot inquire with anyone at my company as they would be none to happy to learn I am dumping M$ :D so I have to figure all this out on my own and this forum has been great so far.  In only 4 days I have my machine at 98% of where I need it to be.

Thanks for the info on CPU stepping!

---

