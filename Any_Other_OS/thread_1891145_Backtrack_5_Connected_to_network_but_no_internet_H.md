---
title: "Backtrack 5 Connected to network but no internet HELP"
date: 2011-12-05
forum: Any Other OS
---

### Post by CJ-1990 on 2011-12-05
G'day people :)

I'm currently having problems using my laptop's internal wireless card to connect to the net.

I've used the terminal to configure and connect to my router, so it does say I'm connected... But it won't let me access any website... 

So far I've tried:

sudo lshw -c network

I found out the logical name of my chipset

ifconfig wlan1 up

I encountered no errors with that

I used the first command again to confirm that my chipset was configured, and it was

I then used iwconfig wlan1 essid (My network) key (Passkey) which worked and connected


But here's where it went wrong.

I then used dhclient wlan1 and got the following error message

No DHCPOFFERS received.

No working leases in persistent database - sleeping.


I don't understand why it's not letting me connect to any website.. I found and configured my wireless card, and successfully connected to the network, yet I can't access any website... 


Thankyou for any help you can offer me, don't hold back on the nerd language, I'm starting to get used to the more complicated terms, and anything I don't know I can just search with my already running laptop.

Cheers

CJ

---

### Post by CJ-1990 on 2011-12-05
I should also note that when I used iwconfig in the console, I was presented with this:

IEEE 802.11bg ESSID: "BigPond475BF2"
Mode: Managed Frequency: 2.462 GHz Access Point: 08:76:FF:47:5B:F2
Bit Rate=48Mb/s Tx-Power=20 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Encryption key:off
Power management:off
Link quality=30/70 Signal lever=80dBm
Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:1 Invalid misc:3 Missed beacon:0

---

### Post by CJ-1990 on 2011-12-05
Here is another error when I input: sudo dhclient wlan1

mv cannot stat `etc/resolve.comf.dhclient-new' : No such file or directory

---

### Post by CJ-1990 on 2011-12-05
I ended up figuring out how to make it work by myself.

Here's how I did it:

After much searching on google with my other laptop running Ubuntu 11.04, I found out how to make it work, I used the following:

sudo iwconfig wlan1 key (My key)

And it worked, I am now connected to the net via my internal wireless card :)

I will now mark this thread as solved.

CJ

---

