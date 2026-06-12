---
title: "no more wireless?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2007-09-05
my wireless card and internet worked perfectly out-of-the-box when i first installed 6 or 7 months ago, but now, after the latest kernel update, nothing i do can get it to come back.  it shows the networks around my house, and even lets me connect to them, but it won't let me get on the internet!  please help!  i REALLY need the internet!

---

### Post by Niklas Schröder on 2007-09-05
anyone?

---

### Post by Niklas Schröder on 2007-09-05
does anyone have a fix for this?  my wireless internet won't work on either the old or new kernel. please help.

---

### Post by Siph0n on 2007-09-05
Well you have to give ppl some information first. I know two of the outputs ppl will probably want are:

ifconfig
and
iwconfig

There is another one like lshw or sometin, but i forget the exact command (it begins with an l and has shw in it lol)

---

### Post by Niklas Schröder on 2007-09-05
ok.  i FINALLY managed to get one of my older live cd's to boot.  here's the output (i'm able to access my wireless router and the internet through the live cd which means, imho, it truly is a kernel issue)...

```

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:9E:97:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:4E:01:6B  
          inet addr:192.168.10.3  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe4e:16b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6746 errors:0 dropped:1 overruns:0 frame:0
          TX packets:4790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8605759 (8.2 MiB)  TX bytes:394767 (385.5 KiB)
          Interrupt:17 Memory:dfbfd000-dfbfdfff 

eth0:avah Link encap:Ethernet  HWaddr 00:14:22:9E:97:96  
          inet addr:169.254.7.125  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:710 (710.0 b)  TX bytes:710 (710.0 b)

```

```

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4C:7E:00:6E   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=21/100  Signal level=-38 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:53

```

---

### Post by Niklas Schröder on 2007-09-06
isn't there anyone out there that can help me with this?  you guys are usually so good at quick replies!  (i wish i knew the answer to it myself, but i'm only helpful in the areas of eye-candy and partitioning.  :p )

---

### Post by Siph0n on 2007-09-06
Sorry I dunno... the output from iwconfig and ifconfig seem good to me. It looks like you are getting an IP from your router (or did u assign this manually?) and you have an internet ip (169.254.7.125) and you see your router (00:90:4C:7E:00:6E)... I am super new, but good luck! :)

---

### Post by Niklas Schröder on 2007-09-06
well what's weird about it is that i can access the networks just fine (see all the networks in the surrounding areas and connect to the ones without passwords), and then it'll show me the signal strength and other things, but it won't let me access the internet.  at all.  it's a kernel issue though because i can get on the internet fine in the live cd (which is what i'm doing now).  any ideas on how to downgrade or re-install the current kernel?

---

### Post by Harpoon on 2007-09-06
From your post it appears that you posted the ifconfig/iwconfig output while you were running the live CD.  However, you need to post the same information taken when you are booted from your hard drive.  Also, you should post what you are running (Edgy/Feisty, 32 or 64 bit), what type of nic.  That helps narrow things down to where someone can actually suggest something relevant.  Shouldn't take too long to get squared away.

---

### Post by dca on 2007-09-06
Are you using ndiswrapper?

---

### Post by Niklas Schröder on 2007-09-06
ifconfig output:

```

eth0      Link encap:Ethernet  HWaddr 00:14:22:9E:97:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:4E:01:6B  
          inet addr:192.168.10.3  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe4e:16b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:658 errors:0 dropped:8 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35966 (35.1 KiB)  TX bytes:4692 (4.5 KiB)
          Interrupt:17 Base address:0x6000 Memory:dfbfd000-dfbfdfff 

eth0:avah Link encap:Ethernet  HWaddr 00:14:22:9E:97:96  
          inet addr:169.254.7.125  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

```

iwconfig output:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4C:7E:00:6E   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-39 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

```

and i'm just using the stock wi-fi program that came with feisty (aka: the little blue bars).

---

### Post by Niklas Schröder on 2007-09-06
```

uname -r

```

turns up...

```

2.6.20-15-generic

```

is this the latest kernel?  and is there anyway to change this without an internet connection?

---

### Post by Niklas Schröder on 2007-09-07
i'm running ubuntu feisty fawn on a dell xps m140 laptop.  at the moment, i'm planning on doing a re-install of the OS to see if that'll do anything.  i've already moved my /home to a different partition and i'm gonna do the work tonight (friday night).  what are the chances this wouldn't work?

---

### Post by Niklas Schröder on 2007-09-08
ok.  -yawns-  i'm going to bed.  but re-installing worked.  night.

---

