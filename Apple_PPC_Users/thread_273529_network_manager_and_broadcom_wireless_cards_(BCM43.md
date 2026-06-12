---
title: "network manager and broadcom wireless cards (BCM4318)"
date: 2006-10-08
forum: Apple PPC Users
---

### Post by jrb114 on 2006-10-08
Hi, 

Yes, I'm trying to get the cursed Airport Extreme to work on my G4 iBook.

I've tried equally on Dapper and Edgy and had the same, strange behaviour.

My wireless network uses WPA, and I can connect to it fine from the command line using wpasupplicant (having installed the firmware from wl_xxxx.o, I've forgotten it's full name).

But, when I try to connect with network manager, it simply doesn't play ball. The dots just twirl around and around, but even the "local" dot, (i.e. the bottom one), doesn't flash green. This implies to me, that network manager can't talk to the card, even though it shows my network in it's list of wireless networks, and gives it a signal strength.

I'm confused, has anybody else seen this strange behaviour?

Thanks,

J

---

### Post by kounavi on 2006-10-09
I will have to confirm that, unfortunately.

I have been trying for **hours** to get this to work, but to no avail.

Let me give you some details:


I am running Ubuntu Edgy PPC, fully updated. 
I have a pre-Feb2005 powerbook, and I've added to it an Airport Extreme Card. This card is -unfortunately- a 4306 Broadcom card, as indicated by my lspci.

I followed every guide I 've found, and I have to tell you, I may not be a kernel hacker but I've been a linux user/admin for quite some years now.

What I get is a very functional "monitor" mode, or anyway, scannind procedure, and no way of actually connecting/associating.

I've been dealing with wireless and linux for 3 yrs now but I have no idea what ths is :confused: ](*,) 

I have tried various firmware versions, and finally extracted my Airport's knowing to work firmware from Tiger Installation DVD. Nothing changed.

In order to be certain that this is the driver's/configuration's fault and not some signal strength or noise thingy, I inserted a cisco 350 pcmcia in my powerbook and tried to make them associate with each other. Needless to say, this is a fail-safe experiment, as far as the signal part is concerned.

I have set my airport's rate to 11M, even messed with iwpriv and swencrypt  (set it to 0, just played with it anyway), removed then reinserted the bcm modules, numerous times, trying to figure out what exactly the problem is.

now let me give you an example:
```
root@litost:~# iwconfig eth2
eth2      IEEE 802.11-DS  ESSID:"koko"  
          Mode:Master  Channel:0  Access Point: 00:40:96:44:00:3C   
          Bit Rate:11 Mb/s   Tx-Power=0 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=-100 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:22   Missed beacon:0
```

This is my cisco card. The numbers are incorrect, but it works.
```

root@litost:~# iwlist eth0 scan
eth0      Scan completed :
          Cell 01 - Address: 00:40:96:44:00:3C
                    ESSID:"koko"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=100/100  Signal level=-164 dBm  
                    Extra: Last beacon: 148ms ago



```

And this one is my Airport scanning.
```

root@litost:~# iwconfig eth0 mode managed
root@litost:~# iwconfig  eth0 essid koko ap 00:40:96:44:00:3C
root@litost:~# iwconfig eth0
eth0      IEEE 802.11b/g  ESSID:"koko"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:40:96:44:00:3C   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




```
Nomatter how I configure it, it just won't work.

It 'sees' there's an AP, attempts association but...

here's an instance of my dmesg:
```
SoftMAC: Authentication timed out with 00:40:96:44:00:3c
bcm43xx: Radio turned off
bcm43xx: DMA 0x0200 (RX) max used slots: 1/64
bcm43xx: DMA 0x0260 (TX) max used slots: 0/512
bcm43xx: DMA 0x0240 (TX) max used slots: 0/512
bcm43xx: DMA 0x0220 (TX) max used slots: 2/512
bcm43xx: DMA 0x0200 (TX) max used slots: 0/512
bcm43xx: PHY connected
bcm43xx: Radio turned on
bcm43xx: Chip initialized
bcm43xx: DMA initialized
bcm43xx: 80211 cores initialized
bcm43xx: Keys cleared
ADDRCONF(NETDEV_UP): eth0: link is not ready
SoftMAC: Authentication timed out with 00:40:96:44:00:3c
```

I even tried a new kernel (2.6.18), in case it has some new 80211 softmac implementation (just in case this is the problem).

I believe I have tried everything.

The only thing I haven't done yet, is switchin to ndiswrapper. But I am not so sure I can do this on ppc. Anyway, I prefer bcm43xx, as an idea.

It even works with kismet. Scanning is so great, I was really excited when I first installed it.

Needless to say, finally, that no gui tool can help either (they only do what's listed above, anyway).

I 've googled up every little warning message, and only ended up to some obscure patch to the 80211 softmac source for the kernel ( in the bcm43xx dev mailing list) , but I dont have the time to get my hands *that* dirty right now.

](*,) :-k :-k

---

### Post by rasec on 2006-10-09
Wow, the ubuntu devs still haven't fixed network manager yet? I posted a bug report along with a fix for this over at launchpad.net a couple of months ago. Too bad they chose to ignore it. 

Anyway, I posted an updated library to fix network manager a while ago. The only problem is that apt thinks its an older version of the library it's replacing, so every time you update your system you'll need to reinstall that package. 

See this thread for more info:

[http://www.ubuntuforums.org/showthread.php?t=230431&highlight=wpa](http://www.ubuntuforums.org/showthread.php?t=230431&highlight=wpa)

---

