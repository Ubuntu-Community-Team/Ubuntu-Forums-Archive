---
title: "Need help with WUSB54G wireless adaptor"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by awd_fan214 on 2006-11-24
i installed the necessary driver and when i run sudo ndiswrapper -l, it says that the driver is installed and that the hardware is detected

however i do not know how to enable the wireless connection and it doesn't show up in my network settings, only wired connection and modem connection show up.  i need help enabling the wireless connection.

Thanks!

---

### Post by PartisanEntity on 2006-11-24
Is your wireless network wpa encrypted?

---

### Post by awd_fan214 on 2006-11-24
i believe it is wep encrypted, not wpa

---

### Post by PartisanEntity on 2006-11-24
I would recommend network manager:

```
sudo apt-get install network-manager-gnome network-manager
```

Reboot and the network manager icon should appear in the top panel. (If it only shows you 'wired' connection then you need to disconnect your ethernet cable).

If you click on the icon you will see all available wifi networks. Click on the one you want and enter the wep data.

---

### Post by awd_fan214 on 2006-11-24
i ran the code to install the network manager, but no icon appeared and i cannot find the manager

---

### Post by PartisanEntity on 2006-11-24
Open a terminal and type:

```
nm-applet
```

Don't close the terminal or it will also close Network Manager (once we have established that this method works we can then add nm-applet to startup and you wont have to load it through the terminal anymore).

You could also 'run' it by pressing alt+f2 and typing 'nm-applet', that way you dont need the terminak open.

---

### Post by awd_fan214 on 2006-11-24
i got this response from that command:

---

### Post by awd_fan214 on 2006-11-24
/bin/sh: /usr/bin/esd: not found

---

### Post by PartisanEntity on 2006-11-24
try alt+f2 and type: nm-applet

---

### Post by awd_fan214 on 2006-11-24
ok, so i got the network manager in the tray, but there is only a wired connection and when remove the ethernet cable i still only see wired connection, but its grayed out, i do not see any option of enabling wireless

---

### Post by PartisanEntity on 2006-11-24
hmm if I remember correctly back when I was trying to set up my wifi connection that's how I did it.

Have you tried right-clicking on the network manager icon to see if you can enable wifi?

Perhaps leaving the ethernet cable unplugged and rebooting might help? (you can tell i was a long time windows user :) )

I am afraid that's the only help I can give you, I am new to this myself.

---

### Post by awd_fan214 on 2006-11-24
sadly, none of that worked, but thanks so much for all your help! ill keep trying to figure something out

---

### Post by rebegin on 2006-12-08
> **awd_fan214 said:**
> sadly, none of that worked, but thanks so much for all your help! ill keep trying to figure something out

hey,
i've got exactly the same problem(in xubuntu 6.10). and it's very strange as i did the same steps(same usb dongle) in kubuntu 6.10 with knetworkmanager and everything went fine...working WPA as well....

in xubuntu i got the
```
/bin/sh: /usr/bin/esd: not found
```
after starting nm-applet in terminal.
please let me know if you've got it working.

---

### Post by rebegin on 2006-12-08
i've got the solution! :D
if you want to use the network manager then you have to set up dhcp in your interfaces file:

```
sudo nano /etc/network/interfaces
```

and edit the eth0 and the wlan0 lines like this:

```
auto wlan0
iface wlan0 inet dhcp
```

good luck

---

