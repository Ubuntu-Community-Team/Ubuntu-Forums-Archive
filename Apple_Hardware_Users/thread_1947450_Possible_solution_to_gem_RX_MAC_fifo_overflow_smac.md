---
title: "Possible solution to gem RX MAC fifo overflow smac errors in dmesg"
date: 2012-03-26
forum: Apple Hardware Users
---

### Post by phila guy on 2012-03-26
ran into this issue where dmesg would be full of
gem 0002:21:0f.0: eth0: RX MAC fifo overflow smac[00810440]
Googled the error message and didn't find a solution aside from taking down the eth0 interface, unloading reloading the gem module and bringing eth0 up again.  

details of my machine which uses a custom 3.0.20 kernel to enable smp. I included gem driver in the kernel, not as a module

```
# cat /proc/cpuinfo
processor       : 0
cpu             : 7400, altivec supported
temperature     : 31-33 C (uncalibrated)
clock           : 500.000000MHz
revision        : 2.9 (pvr 000c 0209)
bogomips        : 49.81

processor       : 1
cpu             : 7400, altivec supported
temperature     : 27-29 C (uncalibrated)
clock           : 500.000000MHz
revision        : 2.9 (pvr 000c 0209)
bogomips        : 49.81

total bogomips  : 99.63
timebase        : 24907667
platform        : PowerMac
model           : PowerMac3,3
machine         : PowerMac3,3
motherboard     : PowerMac3,3 MacRISC2 MacRISC Power Macintosh
detected as     : 65 (PowerMac G4 AGP Graphics)
pmac flags      : 00000014
L2 cache        : 1024K unified
pmac-generation : NewWorld
Memory          : 1536 MB

ethernet card: dmesg fragment just after boot up
[    7.890105] gem 0002:21:0f.0: eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:30:65:c7:95:ca
[    7.890127] gem 0002:21:0f.0: eth0: Found BCM5400 PHY
[   11.499920] gem 0002:21:0f.0: eth0: Link is up at 1000 Mbps, full-duplex
[   28.657236] gem 0002:21:0f.0: eth0: Link is up at 1000 Mbps, full-duplex
[   28.657270] gem 0002:21:0f.0: eth0: Pause is enabled (rxfifo: 10240 off: 7168 on: 5632

```so I tried fooling around with the other settings inspired by this link
[http://fasterdata.es.net/fasterdata/host-tuning/linux/](http://fasterdata.es.net/fasterdata/host-tuning/linux/)

sysctl net.ipv4.tcp_available_congestion_control
gives me
net.ipv4.tcp_available_congestion_control = cubic reno

threw in
/sbin/modprobe tcp_htcp

and added
tcp_htcp
to my /etc/modules to have the tcp_htcp module load on startup

I then added htcp to my congestion control
sysctl -w net.ipv4.tcp_congestion_control=htcp
so that 
net.ipv4.tcp_available_congestion_control = htcp cubic reno

that helped to cut down the
gem 0002:21:0f.0: eth0: RX MAC fifo overflow smac[00810440]
messages. Matter of fact, I only got one overflow message after doing
sysctl -w net.ipv4.tcp_congestion_control=htcp
dmesg gives
TCP htcp registered
after executing above sysctl -w command.

added
net.ipv4.tcp_congestion_control=htcp
to my /etc/sysctl.conf to make it stick.

There is another option to make the overflow messages disappear from dmesg, and that is to disable autonegotiation for the gem interface. I added
pre-up /sbin/ethtool -s eth0 speed 1000 duplex full autoneg off
to my /etc/network/interfaces. Waiting to see how much of an impact turning off flow control has to samba, lusca and upnp on my ancient G4 mac

Update Apr. 3, 2012

Found the culprit that was causing the "eth0: RX MAC fifo overflow smac" in
dmesg on my machine and configuration. One of the caching proxies I was running
had a mis configured disk cache size (totally my fault). It was happily devouring
all the free space I had on my boot drive slowing the disk down and causing the
fifo overflow smac error. Disabled the disk cache and the problem has not
cropped up since.

Stress tested my system by recording 4 High Def (1080i) TV shows simultaneously
using mythtv wrting 4 MPEG2 TS streams to 1 drive. There were no drop offs in
the recordings or 3-5 minute delay from the scheduled recording start and
"eth0: RX MAC fifo overflow smac" did not show up in dmesg. Drop offs in the
recordings and messed up start times were some of the symptoms I was seeing
with the fifo overflow smac error.

So lessons learned:
check disk cache sizes (make sure that you have enough free space in the partitions where your disk cache directories are located and configure accordingly)
hard drive starting to fail (installed smartmontools to keep an eye on the drives I have)
anything else that will do a lot of disk read/writes

---

