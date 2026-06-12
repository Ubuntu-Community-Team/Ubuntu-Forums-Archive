---
title: "Will this work on my ubuntu box?"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by barbz127 on 2006-09-06
[http://www.ht.com.au/area/9642/group/11340/tree/11346/part/M2693/detail.hts](http://www.ht.com.au/area/9642/group/11340/tree/11346/part/M2693/detail.hts)

If not what other gigabit adapters should i be looking at that will work without too much drama.

---

### Post by Chickencha on 2006-09-06
I'm no expert, but I think it should be fine.  Usually you only have to worry about wireless cards, from what I understand.  Anybody can feel free to correct me if I'm wrong.

---

### Post by amo-ej1 on 2006-09-06
So if you need to do this information, you need to find out what the card contains. So you go to the manufacterers website. Offcourse they 'used' somebody elses chipset (it's a Realtek chipset) so you have to get the chipset from the image of the card: ( [http://www.netgear.com/upload/product/ga311/enus_front-hires_product_ga311.tif](http://www.netgear.com/upload/product/ga311/enus_front-hires_product_ga311.tif) )

Now the realtek chip says RTL8169S when you throw that in google you end up with the realtek site which offers downloads for a linux driver: [http://www.realtek.com.tw/downloads/downloads1-3.aspx?software=True&compamodel=RTL8169S-32](http://www.realtek.com.tw/downloads/downloads1-3.aspx?software=True&compamodel=RTL8169S-32)  which means that it will almost certain work out of the box.

---

### Post by barbz127 on 2006-09-10
Cheers,
Just a matter then of taking the linux driver and compiling?

Anything difficult or anything i should know before doing it to get it to work?

Thanks

---

### Post by barbz127 on 2006-09-13
ok - installed it no worries - got it working on my network but a bit slot and found some things in dmesg that i would like an opinion on: (have removed rubbish out of there)


[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
...
[17179595.236000] r8169 Gigabit Ethernet driver 2.2LK loaded
[17179595.236000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 21 (level, low) -> IRQ 193
[17179595.240000] eth0: Identified chip type is 'RTL8169s/8110s'.
[17179595.240000] eth0: RTL8169 at 0xd8a02000, 00:14:6c:83:14:a1, IRQ 193
[17179595.536000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17179595.536000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179595.536000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 209
[17179595.624000] e100: eth1: e100_probe: addr 0x40000000, irq 209, MAC addr 00:02:A5:CB:77:55
[17179595.756000] r8169: eth1: link down
[17179596.116000] Intel ISA PCIC probe: not found.
[17179596.308000] lp0: using parport0 (interrupt-driven).
[17179596.500000] Adding 1150968k swap on /dev/mapper/Ubuntu-swap_1.  Priority:-1 extents:1 across:1150968k
[17179596.632000] EXT3 FS on dm-0, internal journal
[17179596.900000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179596.900000] md: bitmap version 4.39
[17179598.228000] cdrom: open failed.
[17179598.448000] r8169: eth1: link up
[17179598.620000] kjournald starting.  Commit interval 5 seconds
[17179598.620000] EXT3 FS on hda1, internal journal
[17179598.620000] EXT3-fs: mounted filesystem with ordered data mode.
[17179601.272000] ACPI: Power Button (FF) [PWRF]
[17179601.272000] ACPI: Power Button (CM) [PBTN]
[17179601.476000] ibm_acpi: ec object not found
[17179601.524000] pcc_acpi: loading...
[17179603.168000] NET: Registered protocol family 10
[17179603.168000] lo: Disabled Privacy Extensions
[17179603.168000] IPv6 over IPv4 tunneling driver
[17179609.264000] ppdev: user-space parallel port driver
[17179611.572000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179611.572000] apm: overridden by ACPI.
[17179612.208000] ip_tables: (C) 2000-2002 Netfilter core team
[17179612.340000] Netfilter messages via NETLINK v0.30.
[17179612.380000] ip_conntrack version 2.4 (3064 buckets, 24512 max) - 232 bytes per conntrack
[17179613.464000] eth1: no IPv6 routers present
...
[17179649.580000] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.5 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[17179650.788000] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.5 DST=239.255.67.250 LEN=197 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=32769 DPT=16680 LEN=177 
[17179709.588000] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.5 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[17179769.592000] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.5 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[17179829.596000] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.5 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[17179889.600000] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.5 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
[17179917.004000] Inbound IN=eth1 OUT= MAC=00:14:6c:83:14:a1:00:09:f3:74:fb:a2:08:00 SRC=219.224.69.41 DST=192.168.1.5 LEN=60 TOS=0x00 PREC=0x00 TTL=45 ID=26261 DF PROTO=TCP SPT=22374 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 
[17179949.616000] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.5 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 

im a bit worried or curious about the last couple here - what they mean and the down then upping of the nic - but does it look ok?
Thanks
Paul

---

