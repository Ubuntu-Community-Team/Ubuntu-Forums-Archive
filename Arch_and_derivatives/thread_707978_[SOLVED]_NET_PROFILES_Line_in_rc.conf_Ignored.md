---
title: "[SOLVED] NET_PROFILES Line in rc.conf Ignored"
date: 2008-02-25
forum: Arch and derivatives
---

### Post by Majorix on 2008-02-25
I have WPA on a wireless connection, and after a little tinkering, I came to the conclusion that I needed Network Profiles. So I went ahead and created one for the wireless conn and one for the wired.

Everything seemed to work fine (at least on wireless, I haven't tested the wired connection) and I downloaded the updates, and a few extra packages and installed them.

After having installed a GUI and stuff, I rebooted into X. However, when I tried to go onto google on the browser, I couldn't. I tried other pages too, to no avail.

I can connect to the net fine on my desktop however, and I am posting from there.

It came to my attention that, while booting, it didn't even say "Starting the network profile" anymore. I thought it may be something wrong with the rc.conf, so I have tried setting the NET_PROFILES option there to
(wifi !wired)
(wifi)
(menu)
but it didn't work.

I have gone ahead and set the hostname to something else in the main profile (wifi) to see if it would show up (that would mean the line is processed and the profile is working fine, right?), but it went for the default hostname (ie the one in rc.conf) again.

What could be wrong? I am so totally puzzled :(

The line ISN'T commented out.

I tried moving the line to the top but it didn't work.

And finally as a result the wireless device isn't recognized (only lo is).

I want to hear your opinions.

---

### Post by bwtranch on 2008-02-25
Maybe you could post the output of ```
nano /etc/rc.conf 
```
and include some of your info  on the wireless (iwconfig) and just some info on your hardware,...:)

---

### Post by Majorix on 2008-02-26
I can't get on the net on that computer so its impossible for me to post the output of rc.conf. Which specific parts of it you need so maybe I can type them in?

The same with iwconfig :(

My wireless card is an Intel Pro Wireless 2200bg. RAM is 512 and the CPU is 1.73GHz Pentium 4M.

---

### Post by bwtranch on 2008-02-26
> **Majorix said:**
> I can't get on the net on that computer so its impossible for me to post the output of rc.conf. Which specific parts of it you need so maybe I can type them in?

The same with iwconfig :(

My wireless card is an Intel Pro Wireless 2200bg. RAM is 512 and the CPU is 1.73GHz Pentium 4M.

Well, it's ok. I just wish I could look over the file...

I really can't guess the possibilities here. You need to find out if the driver for the wireless is installed and working. Config the thing after that. See in:```
iwconfig
```Your driver comes up? or "no wireless extensions"?

OK bad example. I have no wireless extensions on this machine:
localhost / # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:21:6B:AD:22
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fe6b:ad22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:398206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:432502333 (412.4 Mb)  TX bytes:45263516 (43.1 Mb)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5116 (4.9 Kb)  TX bytes:5116 (4.9 Kb)

localhost / #

I'll have to go to my other machine to show you the wireless out. I have a Belkin.

---

### Post by Majorix on 2008-02-26
It's FIXED now.

It was a bug with a newer version of a software called initscripts in Arch. If you enable testing and update, you are hit by this bug.

I re-installed Arch, but this time I didn't enable testing or unstable. I could update fine and stuff.

When its fixed I will enable testing&unstable again :lolflag: Can't live without the newest software.

Thanks for the help offer, bwtranch :)

---

### Post by kpkeerthi on 2008-02-27
As a side note...
You can keep unstable alongside core and other main repositories without any impact. The packages in testing are uniquely named so they do no conflict with the main ones.

---

