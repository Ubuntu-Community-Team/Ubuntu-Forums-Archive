---
title: "Bluetooth not working on Hardy an Macbook Pro 4.1"
date: 2008-08-26
forum: Apple Hardware Users
---

### Post by pierrelux on 2008-08-26
I bought a wireless mouse (mighty mouse) and tried to get it working using the bluetooth applet first but without success. Then I checked if I had the necessary packages already installed but it seems pretty ok (no backport or whatsoever). 

The adapter is made "visible and connectable for other devices". 

I also set HIDD_ENABLED to 1 in /etc/default/bluetooth

"hcitool dev" shows:
Devices:
	hci0	00:1E:C2:91:64:3A

hcitool scan
Scanning ...
Inquiry failed: Connection timed out

I cannot see any of my bluetooth devices by going in "browse devices" in the menu.

Everything is normal in /var/log/messages

I still have this problem even after a reinstall. I haven't tried it under Gusty.

My mouse worked once, for no reason, just like this, but I cannot understand how it happened. I did absolutely nothing. 

I've been struggling with this quite a lot in the last couple weeks but haven't figured out where the problem is. I found no particular similarities in this topic [http://sudan.ubuntuforums.com/showthread.php?t=786490](http://sudan.ubuntuforums.com/showthread.php?t=786490) but more in this one [http://forum.ubuntu-fr.org/viewtopic.php?id=219824](http://forum.ubuntu-fr.org/viewtopic.php?id=219824) (french).

---

### Post by joe.inom on 2008-08-27
man , now blutooth is the worst , i have wasted $ after $ changing my blutooth devices , but you se i believe it is cheap but still , tahts not teh answer , it is really irritating to have the daily accesory like the blutooth giving distractions.

---

### Post by pierrelux on 2008-09-02
Here's what I found this morning.

By entering sudo hciconfig hci0 reset you should be able to do hcitool scan and then see you device. The applet will then work.

A bug report seems to have been filled about this similar problem but with another device.
[https://bugs.launchpad.net/ubuntu/+s....20/+bug/92111](https://bugs.launchpad.net/ubuntu/+s....20/+bug/92111)

I am still investigating about the problem but I might submit or update a bug report.

---

