---
title: "ethernet stop/start issues"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by md11driver on 2008-01-01
when trying to stop my wifi pc card (ath0) from terminal i type:

"terry@ubuntu:~$ sudo ifdown ath0"

and i see:

ifdown: interface ath0 not configured

i can stop the device by typing:

"sudo ifconfig ath0 stop" but i don't get the desired effects when stopping with this command.

does anyone know how i can configure the device and thus stop it with normal linux commands?

---

### Post by GSF1200S on 2008-01-01
> **md11driver said:**
> when trying to stop my wifi pc card (ath0) from terminal i type:

"terry@ubuntu:~$ sudo ifdown ath0"

and i see:

ifdown: interface ath0 not configured

i can stop the device by typing:

"sudo ifconfig ath0 stop" but i don't get the desired effects when stopping with this command.

does anyone know how i can configure the device and thus stop it with normal linux commands?

how about:

```
sudo /etc/init.d/networking stop
```

Although im pretty sure this will kill all network devices...

Change stop to restart to get it going again...

---

### Post by md11driver on 2008-01-01
thanks for the quick reply.  i entered your suggestion and my machine responded appropriately.  i never lost internet connectivity during the process and the command "sudo ifdown ath0" still returns a message about ath0 not being configured.  if the processes were actually de configured, shouldn't i have lost the internet?  this machine has no wired nic.  i'm confused.

---

### Post by GSF1200S on 2008-01-01
Ok.. lets clarify this as best we can:

Post the contents of the following commands:

```
iwconfig
```

```
iwlist scanning
```

```
ifconfig
```

```
cat /etc/network/interfaces
```

How do you connect to the internet, Ethernet or wireless? After inputing that previous command you could still open web pages and such?? It shuts all internet traffic down for me.

**EDIT** What happens if you run:

sudo ifup ath0

at a terminal?

---

### Post by md11driver on 2008-01-01
i'm getting a forum error message about too many images when i try to put all this info in one post so i'll do one for each input.

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"songbird"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:39:42:91   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-40 dBm  Noise level=-94 dBm
          Rx invalid nwid:27761  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by md11driver on 2008-01-01
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:12:17:39:42:91
                    ESSID:"songbird"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-38 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:40:96:5C:5D:D7
                    ESSID:"apdestpt"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:40:96:5B:F6:31
                    ESSID:"apdestpt"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:18:3F:AA:D0:49
                    ESSID:"2WIRE426"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

---

### Post by md11driver on 2008-01-01
ath0      Link encap:Ethernet  HWaddr 00:15:E9:5E:EA:D9  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fe5e:ead9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1961735 (1.8 MB)  TX bytes:272598 (266.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-15-E9-5E-EA-D9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76318 errors:0 dropped:0 overruns:0 frame:47859
          TX packets:2775 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:8806946 (8.3 MB)  TX bytes:366802 (358.2 KB)
          Interrupt:9 


[/LIST]

---

### Post by md11driver on 2008-01-01
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


i still have internet access after typing all the previous commands.

when i type "sudo ifup ath0"

i get:

Ignoring unknown interface ath0=ath0

i'm feeling that if can get ath0 to respond to ifup and ifdown, my problems would be over.

thanks again

---

