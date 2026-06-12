---
title: "Wireless Card in Virtual PC Session"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by LostSoul on 2006-03-14
Hi There

I'm running Ubuntu (Breezy?) in a Virtual PC session on my XP laptop. From my XP session, I connect to the wireless AP in my house; I've configured my virtual Ubuntu session to use the built-in wireless adapter in my laptop and within Ubuntu itself, assigned the adapter a static IP from my internal address range. When running Ubuntu, I can sucessfully use Firefox, so on the surface of it, everything's groovy. 

There are a few things I don't understand though: when I use the Network applet (the one off the System drop-down menu), it shows me an interface **eth0 **as being active; I would have expected it to indicate a wireless adapter? In XP, I can open my Network Connections and see all adapters, but in Ubuntu, the Network applet only shows me **eth0 **and **Modem**. How can I find out why the installer didn't detect both the wired adapter and the wireless adapter (this is on an IBM t42, btw, so I don't know if that has an impact)?

Thanks

LostSoul

---

### Post by paulmilliken on 2006-03-14
I'm not sure why they didn't show up in the gui.  However, on the command line you should be able to see your wireless hardware with the "iwconfig" command (roughly the wireless version of "ifconfig") - so at least you can check if the gui and the command line are consistent.

---

### Post by LostSoul on 2006-03-15
Paul, thanks for this... I did what you suggested and it gets weirder. If I run iwconfig, I get this:

```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

However, eth0 works just fine because a) I'm writing this message using Firefox inside my Ubuntu session (which, as a long time Windows user makes me feel kinda dirty - in the good way!) and b) when I run ifconfig, I see this:

```

eth0      Link encap:Ethernet  HWaddr 00:03:FF:03:D7:A4
          inet addr:172.16.1.71  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:ffff:fe03:d7a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3608 (3.5 KiB)  TX bytes:1185 (1.1 KiB)
          Interrupt:11 Base address:0xec00

```

Corrcet me if I'm wrong, but it looks like my Ubuntnu ethernet connection is simply jumping on the back of whichever adapter is active in my real-world XP session.

I guess this is a consequence of using Ubuntu inside Virtual PC, but I would love to learn how to install/detect the wireless adapter, and use that. When I installed Ubuntu I saw the wireless tools being installed (and I checked in the package manager, and there they are!) but I don't understand why I'm not seeing a "hard-wired" etherner adapter and wireless adapter too.

Any advice would gratefully received. (And don't feel you have to give step-by-step details if you know of a good post/article you can point me me towards - I've searched this forum but get so many hits that I can't see the wood for the trees).

Thanks

LostSoul

---

