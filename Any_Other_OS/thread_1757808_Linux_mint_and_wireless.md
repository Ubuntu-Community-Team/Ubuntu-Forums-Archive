---
title: "Linux mint and wireless"
date: 2011-05-13
forum: Any Other OS
---

### Post by sunde887 on 2011-05-13
I've tried linux distros a few other times, I've always liked them but I have always had such a hard time getting wireless working that I eventually gave up and went back to windows.

I would really like to try out mint, but I am having trouble(once again) setting up the wireless. I hooked up via ethernet and updated after installing and tried doing "mintwifi" in terminal and still no luck. I'm desperate for help and very unfamiliar with linux.

Please help me out, and let me know what information to provide.

```

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)

```Is part of what I got from lspci, let me know if I should supply all the information it produced.

---

### Post by chrisod on 2011-05-13
In my experience, if your chipset is supported, wireless will just work out of the box. If not, quite frankly it's a lot easier to spend $40 on a USB wireless card that will just work. Try googling the chipset that your wireless chipset that your device runs on and see if anybody else has had luck getting it to work.

---

### Post by wildmanne39 on 2011-05-13
> **sunde887 said:**
> I've tried linux distros a few other times, I've always liked them but I have always had such a hard time getting wireless working that I eventually gave up and went back to windows.

I would really like to try out mint, but I am having trouble(once again) setting up the wireless. I hooked up via ethernet and updated after installing and tried doing "mintwifi" in terminal and still no luck. I'm desperate for help and very unfamiliar with linux.

Please help me out, and let me know what information to provide.

```

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)

```Is part of what I got from lspci, let me know if I should supply all the information it produced.
Hi, I have not used mint linux but in ubuntu you plug the computer into an ethernet connection and go to restricted drivers you should be able to activate the driver you need then restart and you should just have to enter your password.That is also with a bcm 4306 card,so without knowing which card you have it makes it hard to help.

---

### Post by TBABill on 2011-05-13
Possibly try the instructions in the last post of [http://ubuntuforums.org/showthread.php?t=1701618&highlight=rtl8176](http://ubuntuforums.org/showthread.php?t=1701618&highlight=rtl8176)

---

### Post by sunde887 on 2011-05-15
> **TBABill said:**
> Possibly try the instructions in the last post of [http://ubuntuforums.org/showthread.php?t=1701618&highlight=rtl8176](http://ubuntuforums.org/showthread.php?t=1701618&highlight=rtl8176)

I believe I go it mostly working. However, it is quite slow for any websites other than this one and linux mint websites. Any reason why this may be happening?

Not sure if it's helpful, but here is lspci -v
```

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8185
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 3000 [size=256]
    Memory at d4400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl8192CE
    Kernel modules: r8192ce_pci


```Here is the output of iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"AquaDove"  Nickname:"rtl8192CE"
          Mode:Managed  Frequency=2.462 GHz  Access Point: C0:C1:C0:01:E6:BC   
          Bit Rate=72 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=72/100  Signal level=-66 dBm  Noise level=-106 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```And finally iwlist wlan0 scan
```

wlan0     Scan completed :
          Cell 01 - Address: C0:C1:C0:01:E6:BC
                    ESSID:"AquaDove"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=72/100  Signal level=-66 dBm  Noise level=-106 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Extra: Last beacon: 4ms ago


```
Could I have perhaps downloaded the wrong driver? It connects, it's just incredibly slow and most often it times out. I downloaded the rtl8192CE driver. Please help me, thanks.

---

