---
title: "wireless not working"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by frofox on 2006-07-20
I'm new to ubuntu and love it so far, but for some reason I can't get the wireless to work. I'm on a thinkpad t43, and my card is an Intel PRO/Wireless 2915 802.11 a/b/g. I've installed the Wireless Assistant Program, and it recognizes two networks in my area, but I can't connect to either. One is WEP, and I know the right key, and one is unsecured but I still can't connect. Is my card not compatible? 

Thanks for your help.

---

### Post by Paerez on 2006-07-20
I have that card, and it works fine with the "Network Manager" tool. Go to add/remove programs and click advanced and search for network manager. Then log out and back in to gnome and it should be in your notification area.

---

### Post by frofox on 2006-07-20
hmmm, I tried Network Manager, but it doesn't seem to pick up any of the wireless networks. Maybe I'm not using it right...?

---

### Post by monkieie on 2006-07-20
Hi,

have you checked out this link yet?

[http://ubuntuforums.org/showthread.php?t=125150&highlight=wireless+problem](http://ubuntuforums.org/showthread.php?t=125150&highlight=wireless+problem)

---

### Post by Paerez on 2006-07-20
You have to give it a minute or two to pick up all the networks.

Here is how to connect to a network via the terminal to verify that your wireless works:

I am assuming your card is eth1

First check that it exists:
```
ifconfig eth1
iwconfig eth1
```

now lets turn it on:
```
sudo ifconfig eth1 up
```

now lest scan for wireless networks:
```
iwlist eth1 scanning
```

ok lets say we found one called "fluffy"
```
sudo iwconfig eth1 essid fluffy
```

now we need an ip:
```
sudo dhclient eth1
```

now lets see if it worked:
```
ping ubuntu.com
```

---

### Post by Paerez on 2006-07-20
@monkieie: that is for WPA 1&2, and he is reporting a problem with WEP and unecrypted nets, so that doesn't really apply, beyond the very first step which install network manager for him, which I already suggested.

---

### Post by monkieie on 2006-07-20
> **Paerez said:**
> @monkieie: that is for WPA 1&2, and he is reporting a problem with WEP and unecrypted nets, so that doesn't really apply, beyond the very first step which install network manager for him, which I already suggested.

oops sorry - I should pay a bit more attention ](*,)

---

### Post by frofox on 2006-07-20
@paerez:

I tried everything you said, but still can't connect. When I seach for the networks it finds two available, but I can't connect to them.

---

### Post by Paerez on 2006-07-20
can you post the output from those commands so I can see the problem?

---

### Post by PriceChild on 2006-07-20
Have you tried just pasting the network name and settings into system>administration>networking then rebooting... worked perfectly for me.

Whenever i roam, i just use gnome-network-manager

---

### Post by frofox on 2006-07-20
hmm now it's not even recognizing my card...
```

frank@frank-laptop:~$ ifconfig eth1
eth1: error fetching interface information: Device not found
```

---

### Post by Paerez on 2006-07-20
please give me the output of:
```
lsmod | grep ipw
sudo modprobe ipw2200
sudo ifconfig
```

---

### Post by frofox on 2006-07-20
```
frank@frank-laptop:~$ lsmod | grep ipw
frank@frank-laptop:~$ sudo modprobe ipw2200
Password:
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/net/ieee80211/ieee80211_crypt.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/net/ieee80211/ieee80211.ko': No such file or directory
FATAL: Error inserting ipw2200 (/lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

That doesn't look good.

---

### Post by Paerez on 2006-07-20
Hmm you seem to be missing some of the modules. I don't know what you would have to install, since I am at work now, but search through the repos for wireless modules. Its a very generic module, I am surprised its not installed for you.

---

### Post by frofox on 2006-07-20
hmm still nothing. It was recognizing my wireless card, but then I installed automatix, and it seems like it the wireless stopped showing up right after that. Maybe the automatix install deleted a module?

---

### Post by Paerez on 2006-07-21
try installing, or re-installing wireless-tools.

---

