---
title: "Need Help with Internet Configuration"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by lucid on 2005-09-17
[font=Palatino Linotype, serif][size=2]Hi all, I'd appreciate it if you can help me with the following issue:[/size][/font]

  


  [font=Palatino Linotype, serif][size=2]My Internet connection is mostly good (iburst, Kyocera Access Bridge wireless modem), but for some things it times out. This happens when I send emails (tried various clients), click on the inbox link of my yahoo account in Firefox (works on the Windows Firefox), input large slices of text into mud clients (Tinyfugue and SimpleMU), and also when posting to these forums (ducked over to Windows to post this). [/size][/font] 

  


  [font=Palatino Linotype, serif][size=2]I'd be thankful for any suggestions on how to fix this. Cheers. [/size][/font]

---

### Post by lucid on 2005-09-17
I thought I'd post the output from ifconfig in case that helps in diagnosing the issue. Definitely a problem with breaks, as I needed to email myself the output in three different emails because otherwise it wouldn't send with the lot, reboot into windows to come post this. Anyhoo, fun and games. ;)

eth0      Link encap:Ethernet  HWaddr 00:0D:61:93:30:AE 
         inet6 addr: fe80::20d:61ff:fe93:30ae/64 Scope:Link 
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
         RX packets:1037 errors:0 dropped:0 overruns:0 frame:0 
         TX packets:982 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:1000 
         RX bytes:929433 (907.6 KiB)  TX bytes:198804 (194.1 KiB) 
         Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback 
         inet addr:127.0.0.1  Mask:255.0.0.0 
         inet6 addr: ::1/128 Scope:Host 
         UP LOOPBACK RUNNING  MTU:16436  Metric:1 
         RX packets:5534 errors:0 dropped:0 overruns:0 frame:0 
         TX packets:5534 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:0 
         RX bytes:434467 (424.2 KiB)  TX bytes:434467 (424.2 KiB) 

ppp0      Link encap:Point-to-Point Protocol 
         inet addr:203.103.233.233  P-t-P:210.80.1.90  Mask:255.255.255.255 
         UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1 
         RX packets:973 errors:0 dropped:0 overruns:0 frame:0 
         TX packets:885 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:3 
         RX bytes:904127 (882.9 KiB)  TX bytes:165170 (161.2 KiB)

Could there be an issue with formatting affecting the connection?

---

### Post by lucid on 2005-09-18
Or failing a solution, maybe a thought as to what could be contributing to the issue so I can narrow my search. A search for internet/connection problems returns a fair number of hits. :)

---

### Post by Ravilj on 2005-11-02
Hi 

I suggest decreasing your mtu is rather high try:

ifconfig ppp0 mtu 1432

and see if that helps, you can make a permantent change by editing your /etc/pppoe.conf file and add mtu 1432 to the PPP=" " options line.

---

### Post by lucid on 2005-11-03
Thanks for the reply. :) 

I'll hold off on doing that just for now for two reasons: 1. I don't really know what all that means and 2. Last night I installed the latest versions of Firefox and Thunderbird and all (as far as I can tell this soon) of my problems seem to have disappeared. I don't know why as the same issues had occured on other browsers/clients beforehand.

So all good and my last nagging problem with using Ubuntu is gone, which is brilliant. Your help is appreciated, and you've given me something to go learn about which is all to the good. Cheers.

---

### Post by LinuxRules on 2005-11-26
Maybe it will still be a good idea to adjust the MTU anyway

Take a peak at [http://www.iburst.co.za/faq.php#a20]("http://www.iburst.co.za/faq.php#a20") 
where they recommend an MTU of 1352.

Personally I've never had to adjust mine down, but then again I'm less than 1km from the tower, but  have done installations further away where setting the MTU down definitely improved data thru-put [less dropped packets & resends]

---

