---
title: "Ubantu 20.04: WIFI not displayed (Dual boot from USB)"
date: 2021-05-28
forum: Apple Hardware Users
---

### Post by nikkim on 2021-05-28
Hello, I am not an IT guy. I would need help to set up WIFI on  Ubantu which I just installed on my old Mac. WIFI is working on other computers at my place on was working on this MAC before. Thank you

```
lshw -version

    -version        print program version ()

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -json           output hardware tree as a JSON object
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)
    -notime         exclude volatile attributes (timestamps) from output

root@ubuntu:/home/ubuntu# 


```

---

### Post by ActionParsnip on 2021-05-28
what is the output of
```

sudo lshw -C network; lsb_release -a; uname -a; sudo dmidecode -t 1

```
Thanks

---

### Post by nikkim on 2021-05-28
Pleasa see below

```
buntu@ubuntu:~$ sudo lshw -C network; lsb_release -a; uname -a; sudo dmidecode -t 1
  *-network                 
       description: Network controller
       product: BCM4360 802.11ac Wireless Network Adapter
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:18 memory:98600000-98607fff memory:98400000-985fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM57766 Gigabit Ethernet PCIe
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0f0
       version: 01
       serial: ac:87:a3:09:07:2c
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=5.8.0-43-generic duplex=full firmware=57766a-v1.15 ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:98700000-9870ffff memory:98710000-9871ffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal
Linux ubuntu 5.8.0-43-generic #49~20.04.1-Ubuntu SMP Fri Feb 5 09:57:56 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 2.4 present.

Wrong DMI structures length: 2753 bytes announced, only 2535 bytes available.
Handle 0x000D, DMI type 1, 27 bytes
System Information
    Manufacturer: Apple Inc.
    Product Name: iMac14,1
    Version: 1.0
    Serial Number: C02NM13RF8J2
    UUID: d5d5bf82-e68d-f759-917e-7bc5ea06d9cc
    Wake-up Type: Power Switch
    SKU Number: System SKU#
    Family: iMac

Invalid entry length (0). DMI table is broken! Stop.

ubuntu@ubuntu:~$ 


```

---

### Post by grahammechanical on 2021-05-28
Compare what you get when you run lshw -C network with what I get when I run it

> configuration: driver=bcma-pci-bridge latency=0 

> configuration: broadcast=yes driver=rtl8187 driverversion=5.4.0-73-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11

Because I see "broadcast=yes" & "multicast=yes" I know that my wireless adapter has a driver installed and is working. You do not see anything like that. You are dual booting with Windows 10. Is the WiFi adapter turned off in Windows? If it is then WiFi would not be turned on in Ubuntu. When you ran the Ubuntu Live session are you able to use WiFi?

Regards

Regards

---

### Post by tea for one on 2021-05-28
```
 product: BCM4360 802.11ac Wireless Network Adapter
```

Have you had a look at this page with Broadcom info:-

[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by nikkim on 2021-05-28
Please find my answers to your questions:

You are dual booting with Windows 10.  [I]**No, I am doing a dual boot with MAC O/S Catalina**
[/I]
Is the WiFi  adapter turned off in Windows? 
H[I][B]ow can I see if the WIFI adapter is turned off ?
[/B][/I]
If it is then WiFi would not be turned on  in Ubuntu. When you ran the Ubuntu Live session are you able to use  WiFi? H***ow can I enter the Ubuntu Live session***?

---

### Post by nikkim on 2021-05-28
```
[/untu@ubuntu:~$ lspci -nn -d 14e4:
02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
03:00.0 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetXtreme BCM57766 Gigabit Ethernet PCIe [14e4:1686] (rev 01)
03:00.1 SD Host controller [0805]: Broadcom Inc. and subsidiaries BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 01)
ubuntu@ubuntu:~$ 

```


I cannot find the release packages

```

buntu@ubuntu:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal InRelease
Hit:2 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal Release
Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]  
Hit:5 http://archive.ubuntu.com/ubuntu focal InRelease                         
Get:6 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Fetched 228 kB in 1s (301 kB/s)    
Reading package lists... Done
ubuntu@ubuntu:~$ 


```

---

### Post by tea for one on 2021-05-28
[QUOTE=nikkim;14040725]```

02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
```

From [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110), you can find:-
```
14e4:43a0                  bcmwl-kernel-source
```
Open a terminal and enter:-
```
sudo apt install bcmwl-kernel-source
```
Please reboot - any joy?

---

### Post by nikkim on 2021-05-28
Hi, I installed the bcmwl-kernel-source and reebooted the system. Unfortunately, WIFI still does not appear on my network. Do you think it makes a difference, that I have rev.03? Also, I am doing a dual boot, could it be that the information where installed somewhere else other than the bootable drive? Thank you

---

### Post by tea for one on 2021-05-28
> **nikkim said:**
> WIFI still does not appear on my network. Do you think it makes a difference, that I have rev.03? 

Regrettably, I don't know if rev.03 makes a difference.

I suggest that you ask the moderators to move the thread to Apple Hardware or Networking & Wireless for further advice.

---

### Post by nikkim on 2021-05-28
ok, Thank you very much for your help.

---

### Post by nikkim on 2021-05-28
I am sorry, I have one more questions. Do you know how to contact the moderator? Thank you,

---

### Post by slickymaster on 2021-05-31
*Thread moved to **Apple Hardware Users**.*

---

