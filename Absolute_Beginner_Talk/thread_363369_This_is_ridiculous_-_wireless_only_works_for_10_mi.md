---
title: "This is ridiculous - wireless only works for 10 minutes!"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by james957 on 2007-02-16
Hey,

I've got a Dell Precision with the Broadcom 1390 card, and I followed these instructions to install Ndiswrapper: [http://www.ubuntuforums.org/showthread.php?t=297092&highlight=wireless+broadcom+1390](http://www.ubuntuforums.org/showthread.php?t=297092&highlight=wireless+broadcom+1390) (great howto by the way, except for this one problem)

Now my wireless will work for about 10 minutes, then it stops.
I still have a full set of green bars in the upper right panel (showing signal strength), and when I go into network-manager, it shows me connected to the network.

The browser just hangs up.. it says: " Waiting for www.google.com".

The only way to rectify the problem is to reboot.  Disabling the wireless adapter doesn't work, nor does physically turning off the wireless switch on the laptop.

This is getting to be kinda ridiculous.  I really like Ubuntu, but I use wireless all the time adn this is making it unusable for me.  Say what you will about Windows being slow, but at least normal things like wireless work every time, guaranteed, on it.  Geez.

Any ideas?

Thanks,
James

---

### Post by figgles on 2007-02-16
You shouldn't have to disable (and I presume you meant to add "enable") every x minutes. Have you checked out [http://linux-laptop.net/]("http://linux-laptop.net/") for your brand of laptop?

---

### Post by gwpritch on 2007-02-17
Do you have both a wireless and wired nic enabled. If so disable the wired nic. in system>administration>networking. That should solve your problem.

---

### Post by james957 on 2007-02-26
I've tried that, and it's a little better, but the problem hasn't gone away completely.  With the wired interface disabled, the wireless will still stop working every 15 minutes or so... but now deactivating and reactivating the wireless adapter will reset it.
This deactivating and reactivating will keep me connected for a couple hours, but at some point reactivating will no longer reconnect me.  At this point, no wireless networks show up in network-manager, although the signal strength icon in the notification area is a full green bar.


Any ideas?

Thanks,

James

---

### Post by gwpritch on 2007-02-26
post the results of 

```
ifconfig
```

and 

```
iwconfig 
```

---

### Post by james957 on 2007-02-28
gwpritch,

My wireless is currently working, but here's the results anyway..  I'll post the results when the wireless isn't working also.

Working Wireless:

~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:104442 (101.9 KiB)  TX bytes:104442 (101.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:17:31:BB:68:54
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:febb:6854/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:526532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:699967775 (667.5 MiB)  TX bytes:18134927 (17.2 MiB)
          Interrupt:177 Memory:dcffc000-dd000000

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:B6:1B:6C:BD
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by chuckyp on 2007-02-28
Is it possible your laptop is disabling the wireless to conserve on battery power?  You may want to check the BIOS for power management settings for the wireless nic.   Also you can try booting ubuntu with ACPI disabled or fiddling with the power management.

---

### Post by freebird54 on 2007-02-28
Not an expert with either ubuntu, or wireless - but a possible source of problems occurs to me.  Is ipv6 still enabled on your system?  I am not sure of the lease times/etc on ipv6, but connection problems in general seem to result from having it enabled.  A quick flip through these forums would find the relevant commands/locations to blacklist it.

Hope it helps!

---

### Post by gwpritch on 2007-02-28
let's have a look at /etc/network/interfaces.

---

### Post by liljoe76 on 2007-02-28
do you have both ndiswrapper and the nvidia drivers installed?? if so thats probably the issue, is for me anyway. in your logs just after wireless fails look for an irq #xxx (mines 233) that cant be restarted, which would be the conflict between the two drivers. i havent tried reinstalling ndiswrapper so i dont know if the lastest version has fixed this issue. i've also read on here that feisty kernal will solve this issue..... the wait is on, but yea i hear ya, not having reliable wireless is not so much fun.

---

### Post by halfmanhalfbug on 2007-02-28
Hi james957
I had a problem with ndiswrapper's interrupt (IRQ) being disabled for no good reason. The thread is at [http://www.ubuntuforums.org/showthread.php?t=370528]("http://www.ubuntuforums.org/showthread.php?t=370528") 
You can tell if this is happening by doing the following: Open a terminal and enter the following command: ```
dmesg | grep ndiswrapper
```
You should see some information including the IRQ assigned to ndiswrapper. For me this is
```
[   36.502396] ndiswrapper: using IRQ 20
```
Then enter the following command:
```
dmesg | grep "Disabling IRQ"
```
Is that IRQ being disabled? Kernel 2.6.17 has a bug that causes it to disable IRQs when they should not be disabled. If this is your problem you can add parameters to your kernel while booting (edit /boot/grub/menu.lst as described in the above thread) or you can upgrade to kernel 2.6.20. The instructions for upgrading were provided by chili555 in the above thread and work great. The best solution in the long run is to upgrade.
Good luck,
hmhb

---

### Post by james957 on 2007-03-02
Wow.. Thanks for all the suggestions.  I've been on wireless all day for the last couple of days, and it appears to be working now.

A couple things for those who may be having similar problems:

I'm using kernel 2.6.15-28-686.
I do have Nvidia drivers.
I upgraded to the new version of Ndiswrapper (1.37) recently.
I am now disabling the eth0 connection before I establish a wireless connection each time.


Not sure which of these is the source / fix, but if I had to guess, I'd say that it's the disabling eth0 that fixed it.  


Thanks for all your help, and if it craps out on me again, then I'll be back!

James

---

