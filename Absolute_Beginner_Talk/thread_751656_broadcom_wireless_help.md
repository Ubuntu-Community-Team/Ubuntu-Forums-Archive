---
title: "broadcom wireless help"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by AnnAni1234 on 2008-04-10
hello i have a HP dv6250us 
i just recently installed ubuntu gutsy i switched form vista
i have 2 problems 
first
the wireless card isnt working 
second 
the flash player isnt working 

no matter what i try

thanks in advance

---

### Post by Odd-rationale on 2008-04-10
Have you tried going to the Restricted Drivers Manager and installing the drivers there?

What have you tried to get flash working? Have you installed the flashplugin-nonfree package?

---

### Post by bobplano on 2008-04-10
> **Odd-rationale said:**
> Have you tried going to the Restricted Drivers Manager and installing the drivers there?

What have you tried to get flash working? Have you installed the flashplugin-nonfree package?

And if it isn't in the drivers manager, could you post your card here? I don't know if ndiswrapper needs to be installed but it might be needed still

Also for the flash plugin, You need to make sure your multiverse(or restricted, I can't remember) repositories are enabled.

---

### Post by ferdostar on 2008-04-10
> **AnnAni1234 said:**
> hello i have a HP dv6250us 
i just recently installed ubuntu gutsy i switched form vista
i have 2 problems 
first
the wireless card isnt working 
second 
the flash player isnt working 

no matter what i try

thanks in advance

1) Could please tell us which version of Ubuntu do you have (32 or 64 bit)? 
2) Post the output of 
```
lshw -C network
ifconfig
iwconfig
```

---

### Post by AnnAni1234 on 2008-04-11
okay this is what i know

operating system 64 bit

the wireless card 
the restricted drivers say that it is in use
the card model # is BCM94311MCG wlan mini-PCI

output of code
  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:24:04:6E:AE  
          inet addr:172.16.0.101  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe04:6eae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1432059 (1.3 MB)  TX bytes:241061 (235.4 KB)
          Interrupt:10 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

the flashplayer
i have for the repositiies checked main, universe, multiverse and restricted

---

### Post by marcopolo1981 on 2008-04-11
Just done a search in the forums and found this link:

[http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy](http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy)

It tells you how to set up the correct driver
Hope it helps.
Mark

---

### Post by AnnAni1234 on 2008-04-12
i tried it but nothing happened

before i tried the link above i tried
[http://ubuntuforums.org/showthread.php?t=297092&highlight=blacklist](http://ubuntuforums.org/showthread.php?t=297092&highlight=blacklist)
and now it is blacklisted so i dont know what to do

---

### Post by marcopolo1981 on 2008-04-14
[COLOR="Red"]Sorry, but I'm still a newbie to linux.

I use a Broadcom chip also, and I never got it to work in gutsy. I bought an Intel wireless pro card instead, and just forgot I had the Broadcom. It worked immediately in gutsy.
But, I recently upgraded to the Hardy Heron beta, and the Intel chip isn't found at all and the Broadcom chip works straight out-of-the-box. Fixed one to lose the other?!
It's not recommended to upgrade to beta's unless you are prepared to take risks. But if you are, and desperate to go wireless, it might be the way to go. I have had no problems at all with Hardy.

Best of luck, and I hope someone comes up with the fix for you.
Mark
[/COLOR]
Please accept my apologies. My broadcom chip _DOES NOT WORK_ out of the box, and my Intel chip _DOES_. I assumed that it was the other way around because the intel wireless usually has a light that comes on when in use, but it doesn't at all. I thought it must have been using the broadcom chip. Again, please accept my appologies. I will be sure to double-check these things before I post in the future.
Mark

---

### Post by AnnAni1234 on 2008-05-02
i guess that it wasnt updating once i updated the repos then it started working
thanx to all that posted advice

---

