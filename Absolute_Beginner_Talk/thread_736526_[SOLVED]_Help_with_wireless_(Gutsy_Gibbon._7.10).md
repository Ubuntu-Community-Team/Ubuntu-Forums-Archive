---
title: "[SOLVED] Help with wireless (Gutsy Gibbon. 7.10)"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by VyperX on 2008-03-26
Ok, so ubuntu actually detects my wireless card, but I cant connect to the inter via Wireless, I can connect to my neighbor's wireless connection but I cannot connect to mine, ( I know it works because in windows it is working properly)

My laptop is a Toshiba Satellite A215-S4767,
AMD turion 64x2 Dual Core Mobile Technology,
250 gb HDD + 80 gb HDD (external),
ATI Radeon X1200,
54g Atherols Wi-Fi (802.11b/g); 10/100 Ethernet; 4 USB, 1 FireWire, 1 VGA,
1 S-Video, 1 ExpressCard 34/54. 5-in-1 memory card reader,
Realtek High Definition Audio ALC268


Ok, here is a link to another issue I had but I already fixed it , just for reference, you know...

[http://ubuntuforums.org/showthread.php?t=729079](http://ubuntuforums.org/showthread.php?t=729079)

---

### Post by jan quark on 2008-03-26
so if you connects to your neighbor's :) network you can browse the internet and all that fun?

do you have perhaps and encryption enabled?

please post the results of these terminal commands:

```
iwconfig
sudo iwlist scan
cat /etc/network/interfaces
```

---

### Post by ugm6hr on 2008-03-26
After a quick look through the linked thread, I think you have an AR5007 card, and have compiled madwifi with the fix.

As for why you can connect to your neighbour's but not your own access point...

What kind of security do you use on the access point (and what is the router brand / model)?

Important points: Open / WEP / WPA; hide SSID; MAC filtering.

How did you connect in Windows?

What security does your neighbour use?

If you remove all security on home AP, can you connect?

Results of following (and identify your network):
```
iwlist scan
```

---

### Post by VyperX on 2008-03-26
> **jan quark said:**
> so if you connects to your neighbor's :) network you can browse the internet and all that fun?

do you have perhaps and encryption enabled?

please post the results of these terminal commands:

```
iwconfig
sudo iwlist scan
cat /etc/network/interfaces
```

Ok, for iwconfig:

```
diego@Diego-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-93 dBm  Noise level=-93 dBm
          Rx invalid nwid:49549  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by VyperX on 2008-03-26
> **jan quark said:**
> so if you connects to your neighbor's :) network you can browse the internet and all that fun?

do you have perhaps and encryption enabled?

please post the results of these terminal commands:

```
iwconfig
sudo iwlist scan
cat /etc/network/interfaces
```

For sudo iwlist scan:

```
 diego@Diego-laptop:~$ sudo iwlist scan
[sudo] password for diego:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1B:FC:BF:C4:B3
                    ESSID:"Morelos"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-33 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:18:F8:53:D3:50
                    ESSID:"HomePCPros-BB"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0F:66:2A:9B:EF
                    ESSID:"HOME_NY"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:14:6C:A1:C1:00
                    ESSID:"Chanda Home Network"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f0101000e0000
```




For  cat /etc/network/interfaces   is:

```
diego@Diego-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback 
```

---

### Post by VyperX on 2008-03-26
> **ugm6hr said:**
> After a quick look through the linked thread, I think you have an AR5007 card, and have compiled madwifi with the fix.

As for why you can connect to your neighbour's but not your own access point...

What kind of security do you use on the access point (and what is the router brand / model)?

Important points: Open / WEP / WPA; hide SSID; MAC filtering.

How did you connect in Windows?

What security does your neighbour use?

If you remove all security on home AP, can you connect?

Results of following (and identify your network):
```
iwlist scan
```

i can connect on windows because it works (i dont why) I can connect in my neighbor's network because it doesn't have security.

```
 diego@Diego-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1B:FC:BF:C4:B3
                    ESSID:"Morelos"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-34 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:14:6C:A1:C1:00
                    ESSID:"Chanda Home Network"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f0101000e0000
          Cell 03 - Address: 00:1C:10:50:38:8D
                    ESSID:"Broughton"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:18:F8:53:D3:50
                    ESSID:"HomePCPros-BB"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:0F:66:2A:9B:EF
                    ESSID:"HOME_NY"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

```

---

### Post by ugm6hr on 2008-03-27
> **VyperX said:**
> i can connect on windows because it works (i dont why) I can connect in my neighbor's network because it doesn't have security.

How about all the other questions I asked?

I'm afraid I can't help without some information.

Also... in the iwlist scan results - which is your access point?

What happens when you click on the Network Manager icon (top-right, 2 computer screens or 4 narrow grey-blue bars)?

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

---

### Post by VyperX on 2008-03-27
> **ugm6hr said:**
> How about all the other questions I asked?

I'm afraid I can't help without some information.

Also... in the iwlist scan results - which is your access point?

What happens when you click on the Network Manager icon (top-right, 2 computer screens or 4 narrow grey-blue bars)?

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]


Ok, go to this link to see my desktop image... [http://img255.imageshack.us/img255/6213/screenshotdesktoppj9.png](http://img255.imageshack.us/img255/6213/screenshotdesktoppj9.png)

I am actually using wired connection because my neighbor's connection is far away from my house/ computer so he signal is very bad.

''Morelos'' is my wifi

thanks for your help

[IMG]http://img255.imageshack.us/img255/6213/screenshotdesktoppj9.png[/IMG]

---

### Post by ugm6hr on 2008-03-27
Which is **your** access point?

And what happens when you select it in the list?

And what router do you use?

I really can't do much without **lots** more details (see previous posts - esp re: security).

---

### Post by ugm6hr on 2008-03-27
Morelos - OK :)  Good signal strength.  Broadcasting SSID.  Encryption.

What happens when you click on Morelos in that NM drop-down list?

It should ask for a password.  It should also automatically detect what kind of encryption you have.

The most likely issue is that your password is an ASCII code - NM likes HEX codes.

EDIT:
Judging from the lwlist result earlier - you use WEP encryption.
In that case, the most likely issue is the ASCII vs HEX password.
The simplest way to solve this to to just change the password into a HEX passkey (13 HEX digits for 128-bit) in the router settings.  You can then use the same HEX passkey in Windows and Ubuntu.

Or you can use these online generators to create HEX keys from ASCII:
[http://www.csgnetwork.com/wepgeneratorcalc.html](http://www.csgnetwork.com/wepgeneratorcalc.html)
[http://web.sunybroome.edu/~eet168/WebKeyGenerator.html](http://web.sunybroome.edu/~eet168/WebKeyGenerator.html)
Never used them - but they look genuine.

---

### Post by VyperX on 2008-03-27
> **ugm6hr said:**
> Morelos - OK :)  Good signal strength.  Broadcasting SSID.  Encryption.

What happens when you click on Morelos in that NM drop-down list?

It should ask for a password.  It should also automatically detect what kind of encryption you have.

The most likely issue is that your password is an ASCII code - NM likes HEX codes.

Ok, when I click in Morelos it asks my for my password ans when I put the password, it stays loading forever, until it just doesnt load and I need to retype the password. I dont know what you mean by which is my access point

---

### Post by VyperX on 2008-03-29
any help?

---

### Post by ugm6hr on 2008-03-29
> **VyperX said:**
> any help?

Please read my previous post again.

Then supply some of the information asked for in order to help.

Specifically:

Do you use WEP?
If so, is it 64- or 128-bit encryption (if you don't know - how many digits is your password)?
Have you tried using a HEX key (as suggested)?

---

### Post by VyperX on 2008-03-30
> **ugm6hr said:**
> Please read my previous post again.

Then supply some of the information asked for in order to help.

Specifically:

Do you use WEP?
If so, is it 64- or 128-bit encryption (if you don't know - how many digits is your password)?
Have you tried using a HEX key (as suggested)?

Yes I do use WEP, my password has 10 digits and what is the HEX key?

---

### Post by ugm6hr on 2008-03-30
> **VyperX said:**
> Yes I do use WEP, my password has 10 digits and what is the HEX key?

If your WEP password is 10 digits, it should be a HEX password.

I haven't used WEP for about 2 years now, but a quick bit of research revealed that a 64-bit WEP key is 5 ASCII characters or 10 HEX digits.

So presumably your password is made up only of 0-9 and a-f (lower case)? That makes it a HEX (i.e. Hexadecimal) key.

If so, it should work already.  Therefore, it must be Network Manager that is misbehaving - I would suggest trying Wicd instead (see link below).

If not, then repost whether your password is not HEX only.

ALso - I note you started with a statement that you have an Atheros card - but never confirmed.  The output of this command would be useful to ensure I am not missing something bigger (capital C):
```
lshw -C network
```

One other thing - if you want to do things without Network Manager or wicd - this is useful: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by VyperX on 2008-03-30
> **ugm6hr said:**
> If your WEP password is 10 digits, it should be a HEX password.

I haven't used WEP for about 2 years now, but a quick bit of research revealed that a 64-bit WEP key is 5 ASCII characters or 10 HEX digits.

So presumably your password is made up only of 0-9 and a-f (lower case)? That makes it a HEX (i.e. Hexadecimal) key.

If so, it should work already.  Therefore, it must be Network Manager that is misbehaving - I would suggest trying Wicd instead (see link below).

If not, then repost whether your password is not HEX only.

ALso - I note you started with a statement that you have an Atheros card - but never confirmed.  The output of this command would be useful to ensure I am not missing something bigger (capital C):
```
lshw -C network
```

One other thing - if you want to do things without Network Manager or wicd - this is useful: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

```
 diego@Diego-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:0f:da:80
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.3 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wifi0
       version: 01
       serial: 00:1b:9e:28:cd:4d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

---

### Post by VyperX on 2008-03-30
Ok it is now working, thanks a lot, one question more, how do i save this network for that it connects automatically when I start ubuntu?

---

### Post by ugm6hr on 2008-03-30
> **VyperX said:**
> Ok it is now working, thanks a lot, one question more, how do i save this network for that it connects automatically when I start ubuntu?

Perhaps sharing with us how you got it to work might be useful for future readers.

Then mark the thread as solved.

And Network Manager should save the network to connect automatically.  It generally picks secure networks with saved passwords rather than local open networks (I think).

---

### Post by VyperX on 2008-03-31
Ok, how do i mark this as solved? I solved this issue by selecting the HEX option because I tthought that my wifi was another one

---

### Post by ugm6hr on 2008-03-31
It is in thread tools near the top.

I've done it for you this time.

---

### Post by VyperX on 2008-04-02
> **ugm6hr said:**
> It is in thread tools near the top.

I've done it for you this time.

Ok thanks

---

