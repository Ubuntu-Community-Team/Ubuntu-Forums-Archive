---
title: "Stilll having a small problem with WPA"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by vulturesrow on 2005-12-30
Hardware: Dell Inspiron 8100 Laptop, Dlink DI-524 Wireless Router, Dlink DWL-G630(ver C2).

Software: Brand new, fully updated Breezy Badger install including wpasupplicant.

Problem: I followed the excellent WPA howto and it seemed to work like a charm. Upon reboot, I had no connectivity.  I used the following command (from the How-To): 

```
sudo invoke-rc.d networking restart
```

and immediately had full connectivity. Based on the How-To, this seems like the network is being configured before wpasupplicant is being started, but I followed the steps in the how-to to the letter which is supposed to prevent this. The only anomaly I could see in the boot messages is that wpasupplicant appears to try and start itself twice, but I havent been able to figure out why. Any help would be appreciated.

---

### Post by shof2k on 2005-12-30
Which how to did you follow? Cut and paste the web address onto your post so we can see the same instructions.

Can you also display the contents of your interfaces file. To do this Click 'Applications' - 'Accessories' - 'Termina'.  On the command line type
"more /etc/network/interfaces".  Again, cut and paste the results.

Welcome to ubuntu! :)

---

### Post by vulturesrow on 2005-12-30
Shof2k, 

I used the howto from this forum that is posted in the Customization Tips and Tricks forum, the title of which is WPA in Breezy Badger 5.10. 


interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.0.76
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1

iface ath0 inet static
address 192.168.0.76
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid CNRDHome

---

### Post by Lambert on 2005-12-30
modify this part of your interface so it looks like this.

iface ath0 inet static
pre-up wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
address 192.168.0.76
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid CNRDHome

I don't use wpa but a howto on the wiki that says add lines like this instead of the one I inserted. So if what I say doesn't work, modify and try these.

pre-up /etc/init.d/**wpa**supplicant start
pre-up sleep 5

---

### Post by shof2k on 2005-12-30
Thanks for that.  The HOW-TO is at [http://www.ubuntuforums.org/showthread.php?t=90450](http://www.ubuntuforums.org/showthread.php?t=90450) for reference.

Try commenting out the 'iface eth0' to 'gateway' if you're not using a wired network.  If that doesn't help, can you type "dmesg" into a terminal and paste the last page of output.  Also the output from the 'ifconfig' and 'iwconfig' commands.


The solution I did was to disable the "wpasupplicant" script by deleting the symlink, and adding the following lines to your interface file after 'iface ath0'
pre-up /usr/sbin/wpa_supplicant -Bw -i wlan0 -c /etc/wpa_supplicant.conf -D zydas
post-down killall -q wpa_supplicant

You will need to change the parameters to your system, but the idea is the same.

Let me know how it goes.

---

### Post by vulturesrow on 2005-12-30
Gents, 

I tried all your suggestions, and still no luck...Im at a loss..maybe i'll just script in the invoke-rc.d networking restart command. :???:

---

### Post by vulturesrow on 2005-12-31
Gents, 

I have discovered, much to my chagrin, that this is not a WPA problem.  I uninstalled wpasupplicant and went back to my vanilla setup and changed my wireless encryption to WEP. I get the exact same problem, that is, I have a wireless connection, but not connectivity until using the invoke-rc.d networking restart.  I apologize for leading the discussion down the wrong path instead of leaving it opne. Does this perspective help at all?

---

