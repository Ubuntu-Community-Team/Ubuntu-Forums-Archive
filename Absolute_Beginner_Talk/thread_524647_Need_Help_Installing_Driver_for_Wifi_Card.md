---
title: "Need Help Installing Driver for Wifi Card"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by crsd36 on 2007-08-13
I recently purchased an ASUS WL-107G Wireless Cardbus Adapter, but I can't figure out how to compile the drivers that came with it.  There are two tar's that came with it and I cannot figure out how to compile either of them.

---

### Post by Ek0nomik on 2007-08-13
Do they provide you with a README file or anything of the sort?  Perhaps an INSTALL file?  These usually contain instructions.

The install process usually goes something like:

```
cd directoryOfextractedFiles
./configure
make
sudo make install
```

Pasting the contents of the tarball on the forum will be beneficial if the above doesn't work;

```
cd directoryOfextractedFiles
ls -la
```

---

### Post by Bachstelze on 2007-08-13
No need to compile anything, the drivers for this card are included in Ubuntu. Type *sudo iwconfig* in a terminal and paste what you get.

---

### Post by Hospadar on 2007-08-13
Should you need to compile things in the future however, make sure you start off by installing the package "build-essential"
from the command line:
```
sudo apt-get install build-essential
```

---

### Post by crsd36 on 2007-08-13
> **HymnToLife said:**
> No need to compile anything, the drivers for this card are included in Ubuntu. Type *sudo iwconfig* in a terminal and paste what you get.
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"Craig"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:90:4B:3F:C2:1F   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlan1     IEEE 802.11b  ESSID:"Craig"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:90:4B:3F:C2:1F   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=52/70  Signal level=-44 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:320  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:679   Missed beacon:0

irda0     no wireless extensions.

ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by crsd36 on 2007-08-14
> **Ek0nomik said:**
> Do they provide you with a README file or anything of the sort?  Perhaps an INSTALL file?  These usually contain instructions.

The install process usually goes something like:

```
cd directoryOfextractedFiles
./configure
make
sudo make install
```

Pasting the contents of the tarball on the forum will be beneficial if the above doesn't work;

```
cd directoryOfextractedFiles
ls -la
```

Okay, I had no luck following the first part of your suggestion, here are the results:

```
monty@monty-laptop:~/Desktop/RT2500-Linux-STA-1.4.2.0$ ./configure
bash: ./configure: No such file or directory
monty@monty-laptop:~/Desktop/RT2500-Linux-STA-1.4.2.0$ make
make: *** No targets specified and no makefile found.  Stop.
monty@monty-laptop:~/Desktop/RT2500-Linux-STA-1.4.2.0$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
```

It looks like it is missing something for the ./configure to work which is stopping everything else from working?

The contents of the tarball are here:

```
drwxr-xr-x 4 monty monty 4096 2004-08-02 12:23 .
drwxr-xr-x 5 monty monty 4096 2007-08-14 12:05 ..
drwxr-xr-x 5 monty monty 4096 2004-08-17 21:02 Module
drwxr-xr-x 3 monty monty 4096 2004-08-17 20:30 Utility
```

Thanks again!

---

