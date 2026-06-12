---
title: "Stable Madwifi version?"
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by Rog-Mahal on 2008-04-30
I have a 3rd. gen Macbook with the Atheros 5418 wifi card and I'm have some problems with the Madwifi version that I downloaded. I just snagged the current-trunk which was r3563 and I'm getting lots of dropped connections and failed reconnects. Anyone know of a revision that worked especially well for this card?

---

### Post by russo.mic on 2008-04-30
> **Rog-Mahal said:**
> I have a 3rd. gen Macbook with the Atheros 5418 wifi card and I'm have some problems with the Madwifi version that I downloaded. I just snagged the current-trunk which was r3563 and I'm getting lots of dropped connections and failed reconnects. Anyone know of a revision that worked especially well for this card?

Just a tip,  Ive never been able to get that card to work with madwifi, except under 64 bit for some reason!!!  even then, it dropped out on me quite a bit.  

NDISWrapper works great however,  and I recommend you give that a try.  WEP works fine, and it never seems to fail me.

Russo

---

### Post by Rog-Mahal on 2008-04-30
I'm running the 64 bit kernel, so that shouldn't be a problem. I'd like to explore my options using madwifi before I switch over...any thoughts anyone?

---

### Post by mabovo on 2008-04-30
The last one I tested from trunk rv3579 drops frequently like you said.

The one that worked better is rv3545 works without problem.

I was testing everyday snapshot and sometimes one rv worked and the day after not.
I don't know why this happen. There are lots of rv that work with AR5418 and many others are simple a mess.

Probably the next rv will work without problem  :)

---

### Post by Rog-Mahal on 2008-05-01
Thanks, I'll download that one and try it out.

---

### Post by flaggh on 2008-05-02
I've just freshly installed 64-bit Hardy on my macbook2,1 and I'm having a hard time getting madwifi to compile.  Here's the info on my card:

```
$ lspci | grep Atheros
02:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)

```

I've tried downloading the daily build as well as checkout from subversion with the same results when I try to make:
```
harlan@harlan-macbook:~/madwifi$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/harlan/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  UUDECODE /home/harlan/madwifi/ath_hal/x86_64-elf.hal.o
/bin/sh: /home/harlan/madwifi/ath_hal/uudecode: Permission denied
make[3]: *** [/home/harlan/madwifi/ath_hal/x86_64-elf.hal.o] Error 126
make[2]: *** [/home/harlan/madwifi/ath_hal] Error 2
make[1]: *** [_module_/home/harlan/madwifi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

```

Any idea why I'm having problems?

---

### Post by cyberdork33 on 2008-05-02
sounds like incorrect permissions on the source files. What revision is this? You might try a different one.

---

### Post by flaggh on 2008-05-02
The daily snapshot I got from the trunk is r3593-20080502.  Don't know about the one I downloaded from Subversion.  I noticed in the repositories there's a package called madwifi-tools.  Is this what I need or is it something different?

---

### Post by flaggh on 2008-05-02
so the weird thing is I moved the tar file to /tmp in my root filesystem and everything compiled fine so it must be a problem with permissions in my home folder?  I have my home folder setup as an unjournaled hfsplus partition, not to share the home folder with osx, but just to be able to access the files.  Maybe I screwed something up?

Anyways, after compiling I followed the instruction on the macbook wiki again and it still didn't work.

---

### Post by cyberdork33 on 2008-05-02
> **flaggh said:**
> so the weird thing is I moved the tar file to /tmp in my root filesystem and everything compiled fine so it must be a problem with permissions in my home folder?  I have my home folder setup as an unjournaled hfsplus partition, not to share the home folder with osx, but just to be able to access the files.  Maybe I screwed something up?

Anyways, after compiling I followed the instruction on the macbook wiki again and it still didn't work.
Interesting setup to say the least.

Reboot first, if you still have issues, try a different revision. It has been know that newer revisions tend to not work as stated in the wiki:
[https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927](https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927)
r3404 is supposed to work.

---

### Post by flaggh on 2008-05-02
> **cyberdork33 said:**
> Interesting setup to say the least.
Ha! You think that's an interesting setup, you should see my partitioning scheme on my work computer.  Anyways, I think its just an execute permissions problem I probably screwed up somewhere.  Not to get too far off topic, but how do you share files and folders between OSX and Ubuntu?  I'd like the files and folders to be read/write in both OSes.  I never had much of a problem sharing between XP and Ubuntu and I'm new to this whole Mac thing.

> **cyberdork33 said:**
> 
Reboot first, if you still have issues, try a different revision. It has been know that newer revisions tend to not work as stated in the wiki:
[https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927](https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927)
r3404 is supposed to work.
Thanks!  I'll give it a try when I get home and let you know how it works out.  Now that I've managed to get everything else working except for wifi I'm toying with the idea of a fresh install.  It's never as difficult the second time around!

---

### Post by cyberdork33 on 2008-05-02
> **flaggh said:**
> Not to get too far off topic, but how do you share files and folders between OSX and Ubuntu?  I'd like the files and folders to be read/write in both OSes.  I never had much of a problem sharing between XP and Ubuntu and I'm new to this whole Mac thing.I have a shared network drive with all my music, pictures, etc on.

---

### Post by flaggh on 2008-05-03
> **cyberdork33 said:**
> Interesting setup to say the least.

Reboot first, if you still have issues, try a different revision. It has been know that newer revisions tend to not work as stated in the wiki:
[https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927](https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927)
r3404 is supposed to work.

After a fresh install and a little help from this post: [http://ubuntuforums.org/showthread.php?t=772836]("http://ubuntuforums.org/showthread.php?t=772836") everything went smoothly and I'm surfing the net wirelessly as I type this!  Thanks for your help!

---

### Post by flaggh on 2008-05-06
So I need help again.  I screwed up my partition table with disk utility in OSX and rather than try and fix it I decided to go with a fresh install since it was so "easy" to set everything up last time.  I followed the same steps as before, used the same madwifi package as before, and I cannot connect to any wireless networks.  The weird thing is that it detects the card and even see the wireless networks but it won't let me establish a connection to them.

```
harlan@harlan-macbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:2659  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

harlan@harlan-macbook:~$ iwlist ath0 scanning
ath0      Scan completed :
          Cell 01 - Address: 00:14:BF:40:EB:0A
                    ESSID:"Hobbes-USA"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=9/70  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:12:0E:87:3B:70
                    ESSID:"07B408868647"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=9/70  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:18:01:91:F8:8C
                    ESSID:"TF1P5"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=10/70  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 04 - Address: 00:1C:F0:C2:CA:47
                    ESSID:"Imagerlabs Network"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-48 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd070050f202000100
          Cell 05 - Address: 00:16:B6:BE:51:1D
                    ESSID:"carrera"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=14/70  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:09:5B:C2:39:6E
                    ESSID:"ilmonroviawireless"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-42 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

harlan@harlan-macbook:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:17:f2:e7:e6:bc  
          inet6 addr: fe80::217:f2ff:fee7:e6bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:17:f2:31:d8:56  
          inet addr:192.168.20.188  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::217:f2ff:fe31:d856/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:502125 (490.3 KB)  TX bytes:59307 (57.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98800 (96.4 KB)  TX bytes:98800 (96.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-17-F2-E7-E6-BC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8631 errors:0 dropped:0 overruns:0 frame:677
          TX packets:398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:195 
          RX bytes:873052 (852.5 KB)  TX bytes:16964 (16.5 KB)
          Interrupt:17 

```

Any idea why this could be happening?

---

### Post by flaggh on 2008-05-06
Also, I don't know if this is a problem, but shouldn't I expect the ath0 card to show up in my network interface file?

```
harlan@harlan-macbook:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by cyberdork33 on 2008-05-06
try using wicd instead of network manager. A lot of people have been having similar issues and that seems to fix it.

---

### Post by flaggh on 2008-05-06
> **cyberdork33 said:**
> try using wicd instead of network manager. A lot of people have been having similar issues and that seems to fix it.

Thanks!  Fixed it!  Any idea why Network Manager doesn't work?

---

### Post by cyberdork33 on 2008-05-06
> **flaggh said:**
> Thanks!  Fixed it!  Any idea why Network Manager doesn't work?

nope, I just know a lot of people have been complaining about their hardware working, but not being able to connect to anything.

---

### Post by mabovo on 2008-05-06
> **cyberdork33 said:**
> nope, I just know a lot of people have been complaining about their hardware working, but not being able to connect to anything.

Sometimes when battery is low I loose wireless connection. Could be something related to acpi.

---

