---
title: "No internet, yet."
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Irmis on 2007-03-13
I just installed it new, yesterday on me VGN-N130G and everything went perfect until I tried to go online. Its say my wireless card exists (which is good) but its not configured (which bad.) So I type in fields and it says it works but if it is it not talking to me router.

That is a lot more than my WUSB300N from Linksys gets, that is simply ignored. I really hate having to plug into a wireless router, but I can't think of any solutions, besides returning to XP and typing this for help.

---

### Post by siciliancasanova on 2007-03-14
What do you get when you enter:

```
iwconfig
``` and ```
iwlist scan
```?

---

### Post by Skia_42 on 2007-03-14
It's good that your wireless card is recognized. I have found the program NetworkManager to be the easiest wireless network manager to use. Configuring wireless manually is a headache. Follow these steps and you should have wireless in no time.
1) Plug in to your wireless router and get internet
2) Install network-manager
3) type this command into the terminal:
>  sudo gedit /etc/network/interfaces

4)Replace whatever is there with:
> 
auto lo
iface lo inet loopback
auto eth1

5)Do not open System>>>Administration>>>Networking
    You should see a new icon in the upper right hand corner of you screen. That is the network-manager applet. From here on out it's point and click. Hope that helps.

---

### Post by Irmis on 2007-03-14
> **siciliancasanova said:**
> What do you get when you enter:

```
iwconfig
``` and ```
iwlist scan
```?

For
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Home"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:572   Missed beacon:0

sit0      no wireless extensions.

For iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:F8:49:28:8D
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:4
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=99/100  Signal level=-23 dBm  Noise level=-23 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 80ms ago
          Cell 02 - Address: 00:E0:98:E7:30:59
                    ESSID:"05B402217718"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=98/100  Signal level=-27 dBm  Noise level=-27 dBm
                    Extra: Last beacon: 168ms ago
          Cell 03 - Address: 00:0F:66:86:27:FC
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=62/100  Signal level=-70 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 76ms ago

sit0      Interface doesn't support scanning.

---

### Post by oilchangeguy on 2007-03-14
do you see a double screened icon in the panel to the left of the clock? open that, and from the drop down menu select wlan0.

---

### Post by Irmis on 2007-03-14
Yes I do, technically there are two. The one that was always there and the new one I got from following the advice of the second guy. The only bad thing is that the new one only has a selection for a "wired connection" Still nothing wireless.

---

### Post by Irmis on 2007-03-14
The Network Selector found it, and its almost working. If only it would actually connect to the router. One problem after another, I just can't have nice things.

---

### Post by oilchangeguy on 2007-03-14
don't know if this will help. but, have you turned off the router since you loaded ubuntu on your computer? if not try that.

---

### Post by Irmis on 2007-03-14
Just tried that, didn't work. I really hope there is no difference between shared key wep and open system wep.

---

### Post by siciliancasanova on 2007-03-14
For sake of getting your card to work, it's best to just have your system open with no key until you can connect.

---

### Post by oilchangeguy on 2007-03-14
ahhhh. if you've got your router secured, you'll have to enter the security key under wlan0, configure.

---

### Post by Irmis on 2007-03-14
Woo hoo it works now. After I unsecured the router it still didn't work, so I switched to XP to attend class, when I went back to it worked perfectly. Musta needed to restart it, that seems like something I should know.

---

### Post by siciliancasanova on 2007-03-14
Good to see it working, networking is very important as it's kinda tough to get help with ubuntu and install things with out it.  :)

---

