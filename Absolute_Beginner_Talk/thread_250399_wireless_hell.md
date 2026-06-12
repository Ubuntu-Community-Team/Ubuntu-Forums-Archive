---
title: "wireless hell"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by foxjwill on 2006-09-04
So, all of a sudden yesterday my ubuntu box wasn't able to connect to the wlan anymore. I use a WUSB11v4 wireless adapter and a BEFW11S4 wireless router. The router is connected to my Windows XP box. The adapter is connected to my Dapper box via ndiswrapper

```
~$ ndiswrapper -l
Installed ndis drivers:
wusb11v4                driver present, hardware present
```

```
~$ dmesg
[...]
wlan0: no IPv6 routers present
[...]
```

```
~$ lsmod | grep ndiswrapper
ndiswrapper           177364  0
usbcore               130692  8 ndiswrapper,snd_usb_audio,snd_usb_lib,uvcvideo,$
```

```
~$ iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

'iwlist wlan0 scan' does produce nodes, however I'm unable to connect to  
any of them, and my essid (Bach) is not listed.

I tried running 'modprobe -r ndiswrapper' followed by 'modprobe ndiswrapper'. However, every time i run the second command, my computer freezes.

---

### Post by funchords on 2006-09-04
unplug power to your wireless router/ap, then reboot your computer.  After your computer has completed the shutdown half of the reboot, you can restore power to the router/ap.  

if this helps, it's because the router temporarily blacklisted your client for some reason -- or vice versa.  In either case, rebooting clears the blacklist.

---

### Post by Titus A Duxass on 2006-09-04
Alternatively.
Power the pc down, remove wireless interface, power up, power down, replace wireless interface and finally power up.

I have a Edimax card that hangs in the same way and this is my cure.

---

