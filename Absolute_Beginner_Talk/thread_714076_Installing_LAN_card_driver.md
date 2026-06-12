---
title: "Installing LAN card driver"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by ashishkum on 2008-03-03
Hi all

after lots of trying i am not able to install LAN card driver on ubuntu 6.06 i have gcc version 4.0.3. I got one makefile and one .c file with my lan card for linux driver. when i try to compile the .c file it shows lots and lots of errors..

a part of the error is 

sc92031.c:962: error: dereferencing pointer to incomplete type
sc92031.c:963: error: dereferencing pointer to incomplete type
sc92031.c:963: error: dereferencing pointer to incomplete type
sc92031.c:965: error: ‘ENOMEM’ undeclared (first use in this function)
sc92031.c:968: error: dereferencing pointer to incomplete type
sc92031.c:970: warning: passing argument 1 of ‘silan_init_ring’ from incompatible pointer type
sc92031.c:971: warning: passing argument 1 of ‘silan_hw_init’ from incompatiblepointer type
sc92031.c:973: error: dereferencing pointer to incomplete type
sc92031.c: At top level:
sc92031.c:982: warning: ‘struct net_device’ declared inside parameter list
sc92031.c:983: error: conflicting types for ‘silan_tx_timeout’
sc92031.c:377: error: previous declaration of ‘silan_tx_timeout’ was here
sc92031.c: In function ‘silan_tx_timeout’:


i dont know wht to do.and without lan card internet on ubuntu wont work...:(

thankss

---

### Post by jeffus_il on 2008-03-03
What hardware to you have?

output of ```
lspci
``` in a terminal.

---

### Post by ashishkum on 2008-03-03
this is the output of the command

0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AB PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AB ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AB IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AB USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AB SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AB AC'97 Audio (rev 02)
0000:01:0a.0 Ethernet controller: Unknown device 1904:8139 (rev 01)

my lan card is of Tech-COM

---

### Post by jeffus_il on 2008-03-03
Do you know what chip is used on the card?

---

### Post by jeffus_il on 2008-03-03
Seems like some people are not so happy with the card:
[http://www.channeltimes.com/channeltimes/jsp/article.jsp?article_id=70010&cat_id=883](http://www.channeltimes.com/channeltimes/jsp/article.jsp?article_id=70010&cat_id=883)

I you can find out what chip they use there may be a driver available and you won't have to build the driver.

---

### Post by ashishkum on 2008-03-04
i dont know about the chip in which the lan card is inserted. But i have the source file and make file which i got the cd with the driver.I can upload it on my site from where you can download and have a look at it

thanks

---

### Post by jeffus_il on 2008-03-04
It looks like bad code, not just a missing dependency on a header file. Is there a link available to the source on the internet? There are a limited amount of chips they can use for lan cards, there is a good chance that the driver may be in the repository. In the link they claimed to be using a REALTEK8139 but the customer thought otherwise.
Can you read the chip name off the board?

---

### Post by ashishkum on 2008-03-04
give me some time i will read the chip name and will post here i will give the link too to the source code of the c and makefile 
thanks:)

---

### Post by ashishkum on 2008-03-04
hey...

the links for the make file and c file are 

[www.bitsnbytes.org.in/data/makefile.txt](www.bitsnbytes.org.in/data/makefile.txt)
[http://www.bitsnbytes.org.in/data/sc92031.c](http://www.bitsnbytes.org.in/data/sc92031.c)

and sorry abt the chip name i was not able to find

thanksss

---

### Post by jeffus_il on 2008-03-04
Do this in a terminal:```
 lsmod | grep 8139
``` and post the output.
Also run this and post the output: ```
ifconfig
```

---

### Post by ashishkum on 2008-03-04
on running lsmod | grep 8139 there was no output!!!!!

and on running ifconfig here is the output


oot@ashish-desktop:~# lsmod | grep 8139
root@ashish-desktop:~# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

---

### Post by jeffus_il on 2008-03-04
Ok, do a ```
sudo modprobe  8139too
```and then post the output
and then again ```
lsmod | grep 8139
``` and post the output

---

### Post by ashishkum on 2008-03-04
root@ashish-desktop:~# sudo modprobe 8139too
root@ashish-desktop:~# lsmod | grep 8139
8139too                26880  0
mii                     5888  1 8139too
root@ashish-desktop:~# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

root@ashish-desktop:~#


this is the output

---

### Post by jeffus_il on 2008-03-04
Sorry about the edit

also > sudo modprobe 8139cp and > lsmod | grep 8139 and post output.

Run network, I think it is in the system menu to set up your connection.

---

### Post by ashishkum on 2008-03-04
root@ashish-desktop:~# sudo modprobe 8139too
root@ashish-desktop:~# lsmod | grep 8139
8139cp 22528 0
mii 5888 1 8139cp

this is the output....

---

### Post by ashishkum on 2008-03-04
and in network under the system its is not showing any ethernet based connection. so i cant configure it....:confused:

---

### Post by jeffus_il on 2008-03-04
can you do both :  ```
sudo modprobe 8139too 
sudo modprobe 8139cp
```

and see if ```
ifconfig
``` gives a device

and then post ```
dmesg | tail -n 20

```

---

### Post by ashishkum on 2008-03-04
here is the output of all the commands

root@ashish-desktop:~# sudo modprobe 8139too
root@ashish-desktop:~# sudo modprobe 8139cp
root@ashish-desktop:~# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

root@ashish-desktop:~# dmesg | tail -n 20
[17179614.232000] ACPI: Power Button (CM) [PWRB]
[17179614.532000] ibm_acpi: ec object not found
[17179614.600000] pcc_acpi: loading...
[17179621.964000] ppdev: user-space parallel port driver
[17179622.280000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179622.280000] apm: overridden by ACPI.
[17179629.228000] Bluetooth: Core ver 2.8
[17179629.228000] NET: Registered protocol family 31
[17179629.228000] Bluetooth: HCI device and connection manager initialized
[17179629.228000] Bluetooth: HCI socket layer initialized
[17179629.272000] Bluetooth: L2CAP ver 2.8
[17179629.272000] Bluetooth: L2CAP socket layer initialized
[17179629.312000] Bluetooth: RFCOMM socket layer initialized
[17179629.312000] Bluetooth: RFCOMM TTY layer initialized
[17179629.312000] Bluetooth: RFCOMM ver 1.7
[17179684.112000] NET: Registered protocol family 10
[17179684.112000] lo: Disabled Privacy Extensions
[17179684.116000] IPv6 over IPv4 tunneling driver
[17179725.636000] 8139too Fast Ethernet driver 0.9.27
[17179735.060000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
root@ashish-desktop:~#

and network in system is still not showing the device

---

### Post by jeffus_il on 2008-03-04
I thought that the Realtek 8139 driver may be the correct one because the source code identified it, the 8139 drivers load but do not create the device. I will have another look at the source code a little later and see if it builds on my machine.

---

### Post by ashishkum on 2008-03-04
okk thankssss.......:).....

---

### Post by jeffus_il on 2008-03-05
Try ```
sudo modprobe  sc92031
```and see if ifconfig shows the device. This is the module that your source file builds and is available on your system.

Your card is very interesting:
> Beware Intex Is Providing Duplicate Real Tek Rtl 8139d Chip. It Does Not Work In Windows2003 Also. I Downloaded Dirvers From Real Tek Web Site And Contacted China (real Tek). Finally I Contacted Bangalore Intex Office And He Agreed That You Can Return To Dealer And Go For D-link
and
> 
[Here ]("http://www.cnbaforo.com.ar/uploaded/223/1165609892.zip")is the driver for 2.2 and 2.4 provided by the manufacturer. lspci detects the card as a RTL8139, but it´s in fact a Silan SC92031 (it´s a fake cheap chinese card).


Hopefully the driver will solve your problem, it seems to be the right one.

---

