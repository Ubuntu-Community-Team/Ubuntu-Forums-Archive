---
title: "Internet setup"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by fabid23 on 2006-08-30
hi guys,

i just installed ubuntu 6.06 LTS and windows home in the same hard disk. the problem i had is i can not get access to internet on firefox on ubuntu, but i can access internet on windows. the message i recived are:

1, The network device is not installed. which i think may not the one, due to i can get access  to internet on windows.

2, Something about the firewall. which i have totally no idea about it.

so, can anyone help me out?

And another thing is how to install the c compiler in ubuntu?

Thanks

---

### Post by tomBorgia on 2006-08-30
Hiya, Do you have an "ethernet connection" under System > Admin > Network? 

Whats your setup - do you use a gateway/router to get to the internet or do you have a modem or something like that?

---

### Post by funchords on 2006-08-30
What kind of network card do you have?  Make/Model/PCI/USB/Carbus?

---

### Post by fabid23 on 2006-08-30
where can i find what kind of my network is. 
thanks.

also the second message firefox gave me is:
If your computer or network is protected by a firewall or proxy, make sure that Firefox is peritted to access the web

---

### Post by Tantalus90 on 2006-08-30
Best bet is to open the box and have a good hard look at the  network card , there will be identifying numbers either on a sticker or printed on the net card itself

If they are still meaningless feed them into google which with a little bit of trawling should reveal which make and model you are dealing with 

Tant

---

### Post by fabid23 on 2006-08-30
when i use the command : sudo pppoeconf, i get the following message:

Sorry, i scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which control the modem

---

### Post by tomBorgia on 2006-08-30
what does #ifconfig give you? 
pppoe implies your using point to point over ethernet... :-k is that what your trying to do? 

(pppoa [point to point protocol over ADSL] would be a standard ADSL connection - using a ADSL modem...)

if you have a gateway/router connected via ethernet then the pppoe/pppoa will be done at the router, not your PC - in this case you need to set up your (ethernet) network card. 

If not then you will probably have a modem connected via usb (don't know how to help you with that... sorry!)

---

### Post by fabid23 on 2006-08-30
ifconfig gives me the following:
eth0 
Link encap:Ethernet HWaddr 00:14:2A:13:42:D7
inet6 addr: fe80::214:2aff:fel3:42d7/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packet:79 error:0 dropped:0 overruns:0 frame:0
TX packet:18 error:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuel:1000
RX bytes:11784(11.5 KiB) TX bytes:804(804.0 b)
Interrupt:217 Base address:0x2000

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packet:5 error:0 dropped:0 overruns:0 frame:0
TX packet:5 error:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:272(272.0 b) TX bytes:272 (272.0 b)

---

### Post by tomBorgia on 2006-08-30
if you have a gateway/router then try:
sudo dhclient

---

### Post by fabid23 on 2006-08-30
it is working now !!!!!!!!
thanks a lot

---

### Post by krnandak on 2006-08-31
So, how did you get it to work? Could you please explain. I'm in the same quandry!

---

