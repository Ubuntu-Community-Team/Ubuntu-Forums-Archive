---
title: "wifi woes"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by strang3r on 2008-01-25
my usb wifi adapter was working and all of the sudden some debconf poped up and because i typed the wrong things i got no wifi how do i get it back so i can fix what i typed

---

### Post by strang3r on 2008-01-25
any1 help?

---

### Post by (((X))) on 2008-01-25
what d you typed?

---

### Post by strang3r on 2008-01-25
i typed nothing and now it thinks i use the phone line.

---

### Post by strang3r on 2008-01-25
sorry to cause panic but i solved the problem (i think) (-u-);;

---

### Post by strang3r on 2008-01-25
sorry i thought wrong 
code:
zadesktop@zadesktop:~$ iwonconfig
bash: iwonconfig: command not found
zadesktop@zadesktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

zadesktop@zadesktop:~$

---

### Post by strang3r on 2008-01-25
halp!

---

### Post by (((X))) on 2008-01-25
try to push the wireless button(not hold, push)aand wait 30 seconds, til it goes on
your wi-fi is stil there

---

### Post by strang3r on 2008-01-25
its not the wifi per say its the usb its connected to apparently (if i understand correctly)

---

### Post by Het Irv on 2008-01-25
Open Network Settings and make sure that your wireless in enabled and that the settings are correct.  If you are not sure about your settings, Turn on Roaming Mode.

Edit: In Terminal type ```
lsusb
```

Post the results here along with details about your wireless adapter (make, model).

---

