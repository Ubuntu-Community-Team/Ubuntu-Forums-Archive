---
title: "Xubuntu-6.06.1 PPC Doesn't Pick Up Internet"
date: 2008-09-16
forum: Apple Hardware Users
---

### Post by TrikkeDaddy on 2008-09-16
Hi There,
I am testing a live cd (Xubuntu-6.06.1 PPC) on an Apple G3 Blue and white.

Sound works fine, runs good for my taste, but the internet doesn't pick up.

Tried to find out how to autodetect cable but found nothing except the dial up modem.

What can I do now?

Apple Specs


 Machine Name:    PowerMacG3series
  Machine Model:    PowerMac1,1
  CPU Type:    PowerPC 750  (82.2)
  Number Of CPUs:    1
  CPU Speed:    350 MHz
  L2 Cache (per CPU):    1 MB
  Memory:    256 MB
  Bus Speed:    100 MHz
  Boot ROM Version:    1.1.1f4

---

### Post by paul_mcl on 2008-09-16
Which information your internet provider supplied to you? For example: ip, gateway, dns. How do you set up internet connection in another OS?

---

### Post by prshah on 2008-09-16
> **TrikkeDaddy said:**
> 
the internet doesn't pick up.
Tried to find out how to autodetect cable but found nothing except the dial up modem.


Are you using a wired network connection? Then, first you need to check if there are any suitable network interfaces available. Open a terminal (Applications-Accessories-Terminal) and post the output of```
lshw -C network
ifconfig
```
(Ignore the warning about running as super-user).

---

### Post by TrikkeDaddy on 2008-09-16
> **paul_mcl said:**
> Which information your internet provider supplied to you? For example: ip, gateway, dns. How do you set up internet connection in another OS?

Here is my info, gathered from my Windoze computer using the cmd.exe command:

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Valued Customer>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : valuedcustomer
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : 3Com 3C920 Integrated Fast Ethernet
Controller (3C905C-TX Compatible)
        Physical Address. . . . . . . . . : 00-06-5B-AA-5A-8C
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.6
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.254
        DHCP Server . . . . . . . . . . . : 192.168.1.254
        DNS Servers . . . . . . . . . . . : 192.168.1.254
        Lease Obtained. . . . . . . . . . : Tuesday, September 16, 2008 4:09:05
PM
        Lease Expires . . . . . . . . . . : Tuesday, September 16, 2008 5:09:05
PM

C:\Documents and Settings\Valued Customer>

---

### Post by Bikerbob on 2008-09-18
The first question is... are you getting a configured network device?

I tried this install as well and it was not able to find the built in ethernet device on my ppc.

I have since moved on to another form of buntu.. but I think there might be some bug for older mace ethernet devices in the Xubuntu 6.06

James

---

