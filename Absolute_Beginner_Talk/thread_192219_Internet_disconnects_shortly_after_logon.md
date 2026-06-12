---
title: "Internet disconnects shortly after logon"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by SSB on 2006-06-08
I apologize if posting a topic in multiple forums is against the urles, if so I will delete it.. I just don't know where this TRULY belongs >_>

On the live CD my internet worked perfectly so I have no idea what could be causing this...

My internet disconnects about 15 seconds after i log on to the system. Meaning it is connected for the 15 seconds prior to that. I can do anything normally, then it just dies out.

I'm VERY new to Linux so I may be missing something.. I've checked my eth0 connection and it said I had a few error'd packets. None of the networking tools gave me any results (I tried to ping 192.168.1.1 and I got nothing)

Any ideas? Remember that I'm new so the more technical answers I will need some help with. A lot of different things from windows here


I'm connected to my router through ethernet, DHCP is enabled.

---

### Post by hajk on 2006-06-08
You could boot the liveCD and (with internet going perfectly) do the following:

1. Make a copy of /etc/network/interfaces.

2. Run the "dmesg | more" command in a terminal, and look for the driver for 
    your network interface.

3. Make a copy of /proc/modules.

Now, after you reboot the installed OS, the /etc/network/interfaces file should 
look the same way, and the same driver should be installed. It is possible that you need a driver from the restricted-modules package for your kernel, for example 
when you have a wireless card with an Atheros chip (the interface is then called ath0, and the driver madwifi); if so, use Synaptic to install that package.

It may be that all you need to do is run System -> Administration -> Networking
and configure the interface there ("Properties").

In short, a bit of research is required -- that's what makes Linux fun!

---

### Post by verbatim210 on 2006-06-08
can u reconnect?
  
   ..if so, would the 15 minute time limit restart?

---

### Post by SSB on 2006-06-08
hajk, I'll try that in a sec.

verbatim, I can't reconnect. What happens is when the connection dies, it just kind of sits there inactive. The connection should time out but it never gives me a timeout message. Then I try to disable and reenable the hardware, for example, and then I just get a "server not found" error. I'm at a loss.

---

### Post by SSB on 2006-06-08
Ok, here's an update..

The interfaces files on the hard drive is the same as that on the CD.

THe modules file is on the hard drive is empty, the one on the CD has stuff in it. I can't change it because I'm not logged on as owner? Mine is the only account I know of..

The networking options in the CD are the exact same as on the hard drive.

WHAT COULD THIS BE? Should I just try to reinstall and hope for the best?

---

### Post by SSB on 2006-06-09
i got so desperate i reinstalled. of course it did nothing.

---

### Post by verbatim210 on 2006-06-09
lol im also reinstalling my ubuntu.

i think i stuffed up the root admin accounts.

---

### Post by SSB on 2006-06-09
[https://wiki.ubuntu.com/StaticDnsWithDhcp](https://wiki.ubuntu.com/StaticDnsWithDhcp)

I went there, tried it.

I did:

```
sudo nano /etc/network/interfaces
```

The lines read:

> auto eth0
iface eth0 inet dhcp
dns-nameservers 68.94.156.1

Did the command.. errors when trying to restart the network. Still looking for a solution.

---

### Post by musicinmybrain on 2006-06-09
I had almost exactly the same problem.

Try "lspci" in a terminal. If you see that you have a Davicom Semiconductor network interface card, follow the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=186430"). If not... well, good luck!

---

### Post by jvictor on 2006-06-09
Disable IPV6,
Use a static IP if possible
Use ur ISPs DNS server in /etc/resolv.conf

---

