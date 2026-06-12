---
title: "Broadcom wireless driver"
date: 2011-06-14
forum: Any Other OS
---

### Post by akernan on 2011-06-14
I have a Broadcom 4312 wireless card in my Dell laptop.  If I boot to another drive, external usb, and come back my wireless doesn't work.  I can wait a few hours and it'll mysteriously start working. Once it's working I can reboot to this drive and my wireless works.  I checked my hardware drivers, it says the STA wireless driver is activated but not being used.  The system sees my card but not using it.  How can I fix this?

---

### Post by TBABill on 2011-06-14
When you boot to the other drive and then come back to Ubuntu, is it on its own partition or is this a Wubi install? 
 
When you look in the file /etc/modules do you see "wl" in the list? wl is the STA driver module for the BCM4312, unless you are using the b43, which is b43 in modules. Depends on which driver you are using what you should find, but having the right driver listed in that file should enable it on every restart. I have a BCM4312 and my model is only supported by the wl driver, but some models of the 4312 can use either.
 
You can also restart the module by doing ```
sudo modprobe wl
``` and then wait a few seconds, up to about a minute, and then connect. That's not a fix, just reenabling the driver if it's not enabled for some reason.
 
When it happens you can also look at ```
sudo rfkill list
``` and make sure it's not soft blocked. If it says YES, then ```
sudo rfkill unblock all
```

---

### Post by akernan on 2011-06-14
> **TBABill said:**
> When you boot to the other drive and then come back to Ubuntu, is it on its own partition or is this a Wubi install? 

I'm using Mint 10 installed on drive sda, no WUBI.  I have crunchbang, #!, installed on sdc for testing.
 
> When you look in the file /etc/modules do you see "wl" in the list? wl is the STA driver module for the BCM4312, unless you are using the b43, which is b43 in modules. Depends on which driver you are using what you should find, but having the right driver listed in that file should enable it on every restart. I have a BCM4312 and my model is only supported by the wl driver, but some models of the 4312 can use either.

I do not have /etc/modules directory.
 
> You can also restart the module by doing ```
sudo modprobe wl
``` and then wait a few seconds, up to about a minute, and then connect. That's not a fix, just reenabling the driver if it's not enabled for some reason.
 
When it happens you can also look at ```
sudo rfkill list
``` and make sure it's not soft blocked. If it says YES, then ```
sudo rfkill unblock all
```

Here's the output from the commands.  BTW I'm using a DWA-160 that I had, my Broadcom is not working.

```
tony@tony-Inspiron-1564:~$ sudo rfkill list
[sudo] password for tony: 
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
tony@tony-Inspiron-1564:~$ sudo modprobe wl
tony@tony-Inspiron-1564:~$ sudo rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Here's some additional info...
> tony@tony-Inspiron-1564:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
 
tony@tony-Inspiron-1564:~$ sudo iwlist eth1 scan
eth1      No scan results



Here is a screenshot of my additional drivers..

---

### Post by Perfect Storm on 2011-06-15
Moved to Other OS/Distro Talk.

---

### Post by akernan on 2011-06-15
The Broadcom wireless was not working last night when I went to bad but it was when I got up this morning.  Here's some output from iwconfig and iwlist...

```
tony@tony-Inspiron-1564:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:206  Noise level:167
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

tony@tony-Inspiron-1564:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:18:39:89:20:E0
                    ESSID:"home-net"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:5/5  Signal level:-49 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: E0:91:F5:E4:A4:B4
                    ESSID:"ERIC-PC_Network"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-83 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010F1D242CDE4848DAF0994EAC9C13C1A371021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 00:22:75:3E:9F:7A
                    ESSID:"insight_wifi_0627"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-74 dBm  Noise level:-92 dBm
                    IE: Unknown: DD970050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD0022753E9F7A1021000642656C6B696E1023000F463544373233342D342D763130303010240007575053303030311042000E32303930333732333431303632371054000800060050F204000110110020463544373233342D34000000000000000000000000000000000000000000000010080002008C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 04 - Address: 34:EF:44:74:82:E9
                    ESSID:"WIN_832"
                    Mode:Managed
                    Frequency=2.422 GHz (Channel 3)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

tony@tony-Inspiron-1564:~$ 

```

---

### Post by akernan on 2011-06-15
Problem fixed.  I re-installed the patch package.

---

### Post by akernan on 2011-06-16
I found the actual problem.  I used a DWA-160 wireless stick for testing.  The driver made an automated blacklist entry.

---

