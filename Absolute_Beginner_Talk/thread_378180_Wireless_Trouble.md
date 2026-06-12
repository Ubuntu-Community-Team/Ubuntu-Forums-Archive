---
title: "Wireless Trouble"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by shano26 on 2007-03-06
Hey All,

I've been tearing my hair out trying to get wireless working and was hoping someone might be able to help me get it going before I go crazy!

I'm running Edgy (6.10) and haven't been able to get wireless working from the get go. Its installed on a Dell Inspiron 6400 with the Intel(R) PRO/Wireless 3945 Onboard wireless card from what I've read is supported out of the box and indeed it did appear under the System > Administration > Networking section (it did dissappear on me after i did some system updates but reading up on it this seemed due to a kernel change and i've since gotten it back by copying a kernel module from the old kernel to the new one that I found how to do in another post).

The thing is i don't know/can't seem to get it to connect to my wireless router even though it can see it (using iwlist and wifi-radar).

I'll post some of the things that seemed helpful in the other posts. I have mucked around changing things or trying to in some of these like setting essid settings in interfaces etc but have since changed them back (i think) to there defaults.

Output of **iwlist **is as follows: (NETGEAR is the access point i would like to access, no WEP or WPA on atm).

```
shano26@linuxlappy:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:14:6C:96:6D:78
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=92/100  Signal level=-38 dBm  Noise level=-38 dBm
                    Extra: Last beacon: 16ms ago
          Cell 02 - Address: 00:13:46:FF:C2:78
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=37/100  Signal level=-87 dBm  Noise level=-87 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : PSK  
                       Preauthentication Supported
                    Extra: Last beacon: 176ms ago
```

Output of **iwconfig**: (i'm taking it that eth1 is my wireless card!)

```
shano26@linuxlappy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1224   Missed beacon:0

sit0      no wireless extensions.
```

Contents of **/etc/network/interfaces**:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp

auto eth1

auto eth0
```

If any1 could help me out it would be greatly appreciated as i'm at ends with what to do :confused: ! I'm typing this in Ubuntu atm through a cabled connection in the office but would love to be replying with a thanks from the lounge in front of the telly on wireless! 

Cheers,
Shano

P.S I should note that on this same laptop in my Windows XP Media Center boot wireless works fine.

---

### Post by maniacmusician on 2007-03-06
try:

iwconfig eth1 essid "NETGEAR"

or you can use the more manual method of /etc/network/interfaces. I'm going to take my wireless snippet and modify it to contain your info.

Your new file:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid NETGEAR


to restart your networking platform:
sudo /etc/init.d/networking restart

---

### Post by shano26 on 2007-03-07
> **maniacmusician said:**
> try:

iwconfig eth1 essid "NETGEAR"

or you can use the more manual method of /etc/network/interfaces. I'm going to take my wireless snippet and modify it to contain your info.

Your new file:


to restart your networking platform:
sudo /etc/init.d/networking restart

Excellent!! It's now working!! Thank you very much!! :) (i manually modified the interface file btw). 

I think the sudo /etc/init.d/networking restart was the command that did the trick as i did have the wireless-essid NETGEAR in there at one stage but it never seemed to take effect even after a reboot however i never had it quite as nice laid out as your snippet was (i think some of the programs like network manager might have messed around with it when i was trying to get it working) does the order in which the lines appear make a difference? If so that could have been why. My interface file basically looks like your snippet now.

One thing i noticed is that it took a while to time out the eth0 (ethernet) connection when it did the network restart (think it was trying to get an IP address for it). Is this a going to be a problem or make a delay when rebooting the machine or does it always do this anyway in the background?

Going to restart now and see how it goes! Thx again for your quick reply! :popcorn: 

Cheers,
Shano

---

### Post by maniacmusician on 2007-03-07
Well glad to see that some people have their wireless working now :) I don't think the order of the lines makes a difference; however, I always place them there neatly so that anyone editing them in the future doesn't find it hard to understand. 

And yes, if you're not going to be using eth0 (wired cable), you should disable it. You can disable it by putting a # in front of auto eth0 in /etc/network/interfaces

Then, restart your networking again with "sudo /etc/init.d/networking restart" and see if it does the timeout thing again. I'm pretty sure commenting out the auto makes it so that it doesn't load the connection unless you specifically tell it to.

edit: downside to this is that if you ever **do** want to use your wired connection, you'll have to do a  "sudo ifup eth0" to be able to use it.

there's probably a timeout setting somewhere that you should look into. Try "man ifconfig" and see if there's anything in there.

---

### Post by shano26 on 2007-03-07
> **maniacmusician said:**
> 
And yes, if you're not going to be using eth0 (wired cable), you should disable it. You can disable it by putting a # in front of auto eth0 in /etc/network/interfaces

Then, restart your networking again with "sudo /etc/init.d/networking restart" and see if it does the timeout thing again. I'm pretty sure commenting out the auto makes it so that it doesn't load the connection unless you specifically tell it to.

edit: downside to this is that if you ever **do** want to use your wired connection, you'll have to do a  "sudo ifup eth0" to be able to use it.

there's probably a timeout setting somewhere that you should look into. Try "man ifconfig" and see if there's anything in there.

Thanks for that. # it out (i.e #auto eth0) did indeed get rid of the delay and subsequent reboots wireless has been working out of the box and boot time is much faster (i'm guessing eth0 may have been stopping wireless from working even when there was no ethernet connection) and as wireless will be my preffered method I'm not to fussed to have to sudo ifup eth0 when I have to use it.

Now when I'm feeling brave again I might move onto securing the wireless network :eek: .

Thanks again for your replies (i'm feeling a bit foolish for not asking for help sooner :( )

Cheers,
Shano

---

### Post by maniacmusician on 2007-03-07
no problem :) yeah asking for help sooner is always better. Saves you some frustration, and makes someone else feel good because they got  your wireless working. And plus, you learn something in the process.

Life is good..

---

