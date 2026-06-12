---
title: "Ubuntu 22.04.1 LTS on MacBook Air, WiFi not working"
date: 2023-01-05
forum: Apple Hardware Users
---

### Post by branwell on 2023-01-05
Hi,

I'm kind of new to Ubuntu and not an IT guy… Trying to have the WiFi work on my MacBook Air with a fresh install of Ubuntu 22.04.1
The network card is not recognized, and nothing seems to work. I've tried installing drivers to /lib/firmware several times, but apparently, I don't have the correct driver or something.
Here's what a lspci command returns:
```
03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
```
Anyone knows which specific driver I need to install and could provide a link and a simple step-by-step? Please keep in mind I don't have an Internet connection on the MacBook so it needs to be downloaded elsewhere…
Thanks a lot!

---

### Post by howefield on 2023-01-05
Thread movd to the "*Apple Hardware Users*" forum where you are more likely to find people with the same hardware.

---

### Post by tea for one on 2023-01-06
Your device 14e4:43a0 needs bcmwl-kernel-source
Info here [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

In order to install the driver correctly to your PC, I would suggest:-
Share your smartphone connection (tethering) - many internet sites explain this.
Buy a cheap 'n' cheerful Linux friendly USB wireless adaptor - useful to have anyway.
Buy/borrow Ethernet to USB cable

When you have an internet connection on your MacBook Air:-
Boot into Ubuntu 22.04.
Open Software & Updates.
Check that all repositories (main, universe, restricted and multiverse) are active.
Open a terminal and enter the following:-
```
sudo apt install bcmwl-kernel-source
```
Then reboot.

It is possible to download the driver and its dependency packages via another PC.
However, this is a complicated procedure and there are better solutions as I mentioned above.

---

### Post by branwell on 2023-01-06
Thanks for your reply! I guess I'll be buying a USB wireless adaptor&#8230;

---

### Post by branwell on 2023-01-06
Hi, quick follow-up: I found a usb to Ethernet cable I didn't know I had, entered your command, and everything works great! Thanks again

---

### Post by tea for one on 2023-01-06
Splendid.
It is a nice gesture to mark the thread as solved to help other forum members/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Hopefully, you will find your Ubuntu experience even more fruitful than macOS ;).

---

### Post by branwell on 2023-01-07
Yes I did try to find a "mark as solved" button, I couldn't so I gave up&#8230; I think it could be more obvious&#8230;

---

### Post by curtis-s-copeland on 2023-01-27
I lost my functionality on my 4352 when I upgraded to 22.04.  Installed 20(.04?) and the hardware does still work.  I've tried purging bcmwl-kernel-source and reinstalling but it always fails.  Here is the message in the make.log that has been the issue throughout everything I have tried:

DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 5.15.0-56-generic (x86_64)
Fri Jan 27 05:04:12 PM MST 2023
make: Entering directory '/usr/src/linux-headers-5.15.0-56-generic'


  ERROR: Kernel configuration is invalid.
         include/generated/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.


make: *** [Makefile:750: include/config/auto.conf] Error 1
make: Leaving directory '/usr/src/linux-headers-5.15.0-56-generic'

---

### Post by ajgreeny on 2024-09-02
Thread re-opened at request of user with additional solution.

---

### Post by gecd on 2024-09-04
I was able to work around this without a USB to Ethernet adapter:

1. On my mobile phone, I set up the hotspot as an open (no password) wi-fi
2. I connected the MacBook to the hotspot - it worked
3. I ran [COLOR=#000000][FONT=&quot]sudo apt install bcmwl-kernel-source[/FONT][/COLOR]
4. After this, I connected to the secured wi-fi -- it worked

Hope this helps.

---

### Post by ajgreeny on 2024-09-04
Old thread now re-closed following the final post for which it was reopened to allow new information to be added..

---

