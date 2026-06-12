---
title: "Macbook 1,1 Airport trouble"
date: 2010-01-21
forum: Apple Hardware Users
---

### Post by Elektor- on 2010-01-21
Hello,

I'm having difficulty with my wireless connection under 9.10. I had just finished setting up my connection to be a static IP with port forwarding on my router by editing the /etc/network/interfaces from the default to :
> auto lo
iface lo inet loopack
iface wlan0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1And got the port forwarding working fine through the router after editing the settings... until I rebooted. 

Now under the wireless networks tab on the top bar it says "device not managed" and no wireless networks are appearing. What is even stranger is that when I go into my network connections under wired connections there is a new network named "ifupdown (wlan0)" that I cannot remove or edit. 

I've tried to do a search to find information about the problem (or how to reinstall the drivers) but as the wireless for macbook 1,1's is supported out of the box I haven't been able to find anything. That being said, any suggestions or help would be greatly appreciated!

---

### Post by linuxopjemac on 2010-01-22
I would first uninstall the network manager, which can make your life difficult:

```
sudo apt-get remove network-manager network-manager-gnome
```

Then you change /etc/network/interfaces to:

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.2.2
netmask 255.255.255.0
(with or without)network 192.168.2.0
(with or without)broadcast 192.168.2.255
gateway 192.168.2.1
```

then restart networks or reboot:

```
sudo /etc/init.d/networking restart
```

---

### Post by Elektor- on 2010-01-22
Well assuming I followed that I would have no gui network manager.. So what would I need to run in terminal to connect to the network (as I'm sure it wont auto connect to a secured network)? 

Alternatively, if I don't need to connect through terminal, what would be the next step? 



Thank you!

---

### Post by linuxopjemac on 2010-01-22
oops, ok, I don't know how to setup the config file for WPA. Cannot you delete that config file and set everything from within the networkmanager?

---

### Post by Elektor- on 2010-01-22
That's what I tried to do first but I couldn't get the static IP working correctly so I had to go in and deal with the /etc/network/interfaces file. Like I said, both the port forwarding and static IP were working fine with the edited config until rebooting. That makes me think that theres just some minor tweak that I need to make somewhere to fix it. 


Just out of curiosity though, how would you connect eth0 (for example) to a network through the terminal?

---

### Post by linuxopjemac on 2010-01-22
> Just out of curiosity though, how would you connect eth0 (for example) to a network through the terminal? 

if all settings in /etc/network/interfaces are correct for eth0

```
sudo ifup eth0
```

to get back to the subject, I would google /etc/network/interfaces, WEP or WPA, and hidden SSID to find a suitable config file. Do you use WPA or WEP to secure the connection ?

---

### Post by Elektor- on 2010-01-22
Ok, I'll have to do a little research then - I'm using WPA personal security on the router. 

I'm thinking about booting into ubuntu (on osx atm) and using eth0 to do an apt-get update for the networking manager packages to see if that helps. I might have accidentally messed up some sort of setting in there that reinstalling may fix.

---

