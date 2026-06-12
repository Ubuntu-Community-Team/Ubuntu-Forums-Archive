---
title: "Wireless Connections"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by mc.7winkie on 2007-01-22
I recently got Ubuntu up and running and installed my drivers through ndiswrapper.  I though I had everything going good until I tried to connect to the internet.  I couldn't.  I know my network doesn't have any passwords per se but uses mac filtering and unless MAC addresses change based on operating system then everything should be going good.  It just isn't.  I have my USB wireless card set as the wlan0 and it just can't seem to connect to my network.  Any solutions?

---

### Post by Atomic Dog on 2007-01-22
The unit is activated in Networking?  The wlan is enabled and the correct SSID and WEP password is setup?  Should work.

Do/check the settings.  Reboot and see what the terminal command "ifconfig" has to say.

---

### Post by jimrz on 2007-01-22
> **mc.7winkie said:**
> I recently got Ubuntu up and running and installed my drivers through ndiswrapper.  I though I had everything going good until I tried to connect to the internet.  I couldn't.  I know my network doesn't have any passwords per se but uses mac filtering and unless MAC addresses change based on operating system then everything should be going good.  It just isn't.  I have my USB wireless card set as the wlan0 and it just can't seem to connect to my network.  Any solutions?

check in "Networking" on the DNS tab and make sure that proper ones are listed. for some reason this does not alway happen automatically on initial install.

---

### Post by moshuptrail on 2007-01-22
try turning off the MAC addr filtering temporarily
turn off wep or any other security so you know that's not a factor

---

### Post by mc.7winkie on 2007-01-23
I tried to ifconfig and iwconfig commands and it does not appear to be connecting me to my networks SSID.  Those commands show that everything lloks like it's working except that all the things that appear to look as changeable setting (i.e. power management, channel, essid) are set to off or 0.  I'm not sure what to do.  I followed the instructions on this guide save for the installing ndiswrapper. 
[http://www.gidforums.com/t-4390.html](http://www.gidforums.com/t-4390.html)
I'm not completely sure though what to do.  I also was unable to do the steps after the first modprobe command.  Oh yeah, I know that my ISP uses dynamic IPs but that hasn't ever stopped me before in windows.

---

