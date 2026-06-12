---
title: "Networkcard Intel Pro/10+ not working"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by cvanstic on 2007-05-20
Hi,

I recently installed Ubuntu 7.04 on an older PC (Pentium III 123,2 MB Ram)

After the initial problem of booting from the CD (BIOS is < 2000) , using a Smartboot disk I managed to install the OS on my PC.

One step always failed, namely the detecting networkcard (which is an ISA Intel Pro/10+). Also the consequtive installation step where I could choose the correct driver didn't solve the issue (network card remained undetectable). So to progress I have chosen [COLOR="Blue"]'dummy' [/COLOR]as networkcard and manually configure the IP of my system, subnet mask and gateway (my router's IP)

After searching on the internet I have found how to force (autodetect=1) to get my network card detected during boot. Under the GRUB recovery boot I see that my card has been decivered as the right one 
So far so good (I guess) but within the rebooted system I still do not get a network connection.
First I've deleted the "dummy" networkcard and replaced it with eth0 representing my configured card, but this did no do the thing (below is an extract of the System log messages on boot)

May 20 09:41:35 CVS9901 kernel: [   29.963430] isapnp: Scanning for PnP cards...
May 20 09:41:35 CVS9901 kernel: [   30.116251] isapnp: Card 'Intel PRO/10+ or compatible adapter'
May 20 09:41:35 CVS9901 kernel: [   30.116265] isapnp: 1 Plug & Play card detected total

May 20 09:41:36 CVS9901 kernel: [   63.405875] eepro_init_module: Auto-detecting boards (May God protect us...)
May 20 09:41:36 CVS9901 kernel: [   63.425805]  at 0x210, 00:a0:c9:22:a7:06, IRQ 10, 10BaseT.
May 20 09:41:36 CVS9901 kernel: [   63.430617] eepro.c: v0.13b 09/13/2004 [email]aris@cathedrallabs.org[/email]
May 20 09:41:36 CVS9901 kernel: [   63.527303] lp0: using parport0 (interrupt-driven).

May 20 09:41:36 CVS9901 kernel: [   63.638187] Adding 361420k swap on /dev/disk/by-uuid/95690e6a-8d3c-4390-b724-3e4621cd075e.  Priority:-1 extents:1 across:361420k
May 20 09:41:36 CVS9901 kernel: [   63.850543] EXT3 FS on hda1, internal journal
May 20 09:41:36 CVS9901 kernel: [   64.548291] eth0: multicast setup failed.
May 20 09:41:36 CVS9901 kernel: [   64.548851] eth0: multicast setup failed.
May 20 09:41:36 CVS9901 kernel: [   64.548937] eth0: multicast setup failed.
May 20 09:41:36 CVS9901 kernel: [   64.788362] NET: Registered protocol family 10
May 20 09:41:36 CVS9901 kernel: [   64.788722] lo: Disabled Privacy Extensions
May 20 09:41:36 CVS9901 kernel: [   64.789188] eth0: multicast setup failed.
May 20 09:41:36 CVS9901 kernel: [   64.789313] eth0: multicast setup failed.

What I notice is that the multicast failed but ??

running ifconfig shows:
eth0      Link encap:Ethernet  HWaddr 00:A0:C9:22:A7:06  
          inet addr:192.168.123.251  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:c9ff:fe22:a706/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)
          Interrupt:10 Base address:0x210 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4680 (4.5 KiB)  TX bytes:4680 (4.5 KiB)

Can anybody shed more light on this?

---

### Post by 56seeker on 2007-05-20
I'm no expert but I read "multicast set up failed" as to mean DHCP set up failed. You did say you'd manualy configured your net card?

I'm not familiar enough with the system to know if this could be a standard error code from a driver that expects to be using DHCP but is manualy configered.

---

