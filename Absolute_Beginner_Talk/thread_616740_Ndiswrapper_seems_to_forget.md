---
title: "Ndiswrapper seems to forget"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Superdelphinus on 2007-11-18
after using ndiswrapper with the windows driver for my wireless card everything works perfectly but when i reboot the option to select wireless disappears and i have to go through the whole process of installing the .inf file again. I just want to be able to turn the computer on and it just log on to my wireless network! any ideas?

---

### Post by celticbhoy on 2007-11-18
How are you installing the driver.
Post a fulllist of the commands you use.

---

### Post by Superdelphinus on 2007-11-18
oh erm i don't use a command line i just open ndiswrapper and then browse to a copy of the relvant .inf file. When i reboot even though ndiswrapper says that the oem7.inf driver is loaded and hardware is present wireless isnt present in the network manager. i have to uninstall then install again every time

---

### Post by Superdelphinus on 2007-11-18
anybody?

---

### Post by nick_h on 2007-11-18
After the reboot try the following commands in a terminal:
```
ndiswrapper -l
```
From what you are saying this should say that the driver is loaded and the hardware present.
```
iwconfig
```
Does the interface appear here?

---

### Post by Superdelphinus on 2007-11-19
Thanks, i'll check that out later
If i load ndiswrapper it says the hardware is present but there's no option for wireless in the network manager, only wired and modem - until i uninstall and reinstall again!

---

### Post by Superdelphinus on 2007-11-26
tom@tom-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This is what it says on reboot. it looks like it's all installed but it's just that the option to use wireless isnt in the network manager until i uninstall then reinstall again

any ideas?

---

### Post by Superdelphinus on 2007-11-26
Help Me Please!!

---

### Post by erm27 on 2007-11-26
I see there is a switch for ndiswrapper -m (writes modprobe configuration)

have you run sudo ndiswrapper -m?

Include any errors you might encounter during bootup
(syslog?)

---

