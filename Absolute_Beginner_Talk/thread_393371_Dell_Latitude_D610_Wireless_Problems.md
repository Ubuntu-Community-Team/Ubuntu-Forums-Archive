---
title: "Dell Latitude D610 Wireless Problems"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by dhtseany on 2007-03-25
Hi guys, 
I got a messed up problem here..

I had installed Ubuntu 6.06 Dapper on my Dell Latitude D610. This was my first real Linux installation that i've stuck with for more than a week. After a while my computer was super cluttered with a bunch of stuff that I'm 100% sure I didn't need to run Ubuntu. And then I was attempting to use WPA keys so I installed network manager. I didn't seem to work at all and I uninstalled it and tried reverting back to the stock network-admin. But since then my wireless hasn't worked. Figuring I messed stuff up big time I decided it was time to just wipe the HDD and reload a clean install, only installing software I actually use (and hoping that my wireless would be reinstated).

Well... 

Not so much. Everything reinstalled fine, but my wireless never came back. Now I'm talking about a 100% formatted HDD; nothing left at all. I was reading on a few other posts and they suggested to try the following to see if Ubuntu picked up my card on its own (and I think it did):

```

sean@ub-laptop:~$ lspci | grep Intel*
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express P rocessor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GM L Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Expre ss Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FR W (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge  (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller ( rev 03)
[b]0000:03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
[/b]

```

So tell me, does this mean that Ubuntu did detect my wireless? Am I missing drivers? Any ideas what is wrong?

Thanks in advance,
Sean

---

### Post by Kamu on 2007-03-25
Please go to a terminal and run the command iwconfig and paste the output.  Also paste the content of the file /etc/network/interfaces

---

### Post by dhtseany on 2007-03-25
ifconfig:
```
sean@ub-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:CF:41:09
          inet addr:88.17.92.4  Bcast:88.17.92.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fecf:4109/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:34242704 (32.6 MiB)  TX bytes:5594539 (5.3 MiB)
          Interrupt:169

eth1      Link encap:Ethernet  HWaddr 00:16:6F:18:FD:46
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Memory:dfcff000-dfcfffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

```

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid snellnet
wireless-key C297DC2A9D

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by Kamu on 2007-03-25
Well, that's the output of ifconfig... which does indicate two network interfaces so yes it seems detected.  Can you please paste the output from iwconfig (w, not f) which gives wireless specific information.  I think it will be a bit more useful in this case.

---

### Post by dhtseany on 2007-03-25
sean@ub-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      radio off  ESSID:"snellnet"
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by dhtseany on 2007-03-26
In case anyone else ran into this problem and are looking for an answer, I figured out what was wrong. After reviewing the contents of "iwconfig" I realized that radio was set to off, indicating that the wireless was turned off. I have a function key that turns it on and off, and i'm assuming my cat probably walked on the keyboard and somehow hit it (its a long shot but the only thing i can think of:))

Anyways, for a D610 the function key Fn+F2.

Take care and thanks for the help


Sean

---

