---
title: "Wireless problems"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by JohnO'L on 2007-02-17
Hi Guys

I'm a complete Linux numpty trying to set up my wireless connection........

I've installed Ubuntu 6.1 on my IBM T41 Thinkpad, working fine on a wired connection to my ADSL router but can't get the wireless card to work correctly, I think I know the problem, described below but have no idea how to fix it !!!

johno@johno-laptop:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

johno@johno-laptop:~$ lshw -businfo -C network
WARNING: you should run this program as super-user.
Bus info     Device    Class          Description
=================================================
pci@02:01.0  eth0      network        82540EP Gigabit Ethernet Controller (Mobile)
pci@02:02.0  wifi0     network        AR5212 802.11abg NIC 

Seems it's getting confused as to which device name to use !!! think maybe the system->networking GUI is configuring ath0 whilst the device should be wifi0...

Hope this makes sense and all help would be appreciated

Thanks

---

### Post by jpeddicord on 2007-02-17
Actually, it is naming it correctly. 'ath' stands for Atheros, a chipset used in many wireless cards. If an atheros driver is available, the system will use ath0 instead of wifi0. In all other cases, wifi0 is used.

Jacob

---

### Post by JohnO'L on 2007-02-18
Thanks Jacob,

As you can see ath0 has wireless extensions but lshw reports back:

pci@02:01.0 eth0 network 82540EP Gigabit Ethernet Controller (Mobile)
pci@02:02.0 wifi0 network AR5212 802.11abg NIC
 
i.e. no ath0 !!! any thoughts ?

---

