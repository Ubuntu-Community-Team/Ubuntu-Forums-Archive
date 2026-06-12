---
title: "setting up wifi-radar on a fresh install"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-09-23
i'm attempting to set up wifi-radar, but am not able to connect to a network with it. i can, however, connect to a network through system>networking. whenever i try on wifi-radar, it either says it worked, but the "connected to" network is wrong or not showing. i've heard that commenting out the interfaces file will help, but i commented all the lines out to no avail.

is there a trick to getting it set up? thanks!

---

### Post by digitalhav0c on 2006-09-23
What did when it gave me that error was disconnect then reconnect it worked for me.

---

### Post by shanepardue on 2006-09-23
i've disconnected and reconnected many times. any edit on the interfaces config?

---

### Post by blx_286 on 2006-09-23
> **shanepardue said:**
> i'm attempting to set up wifi-radar, but am not able to connect to a network with it. i can, however, connect to a network through system>networking. whenever i try on wifi-radar, it either says it worked, but the "connected to" network is wrong or not showing. i've heard that commenting out the interfaces file will help, but i commented all the lines out to no avail.

is there a trick to getting it set up? thanks!

That was how all my trouble started :p  Tried the wifi-radar but it wouldn't connect and then I couldn't connect. Tried the commenting out the interfaces and stuff, but couldn't get my WG111 back online.

Went and bought a AirLink AWLC5025 and can't get it setup at all ](*,)

---

### Post by plexi50 on 2006-09-24
No need to do the comment out lines thing. Just put those back to the way they were, and make sure you can connect by configuring System/Admin/Networking. If you can, then take out the sys id/and passcode/hexcode...leave them blank. May have to reboot and make sure network is not connected. Then open wifi radar and configure the connections there, no need to use networking at all, let wifi handle the job 100%. If you have a hidden sys id, just go to new and set it up.

---

### Post by jimrz on 2006-09-24
> **shanepardue said:**
> i'm attempting to set up wifi-radar, but am not able to connect to a network with it. i can, however, connect to a network through system>networking. whenever i try on wifi-radar, it either says it worked, but the "connected to" network is wrong or not showing. i've heard that commenting out the interfaces file will help, but i commented all the lines out to no avail.

is there a trick to getting it set up? thanks!

Never tried wifi radar, but your info says "Ubuntu 6.06 user" so are you using Gnome?  If so, try network-manager. It works quite nicely on my laptop. Takes a little work to get setup properly, but it is not difficult and there is plenty of info on it both here on the forums and on the wiki to guide you.

---

### Post by shanepardue on 2006-09-24
i followed the directions provided for getting wifi-radar to work and it still won't let me connect. it either says it got an ip and doesn't really or it says it didn't get an ip. either way, no internet.

as far as the network-manager idea, i did try that and i couldn't get that to work properly either. i do suppose it's better chance of someday getting it to work since it's more popular, but i did get pretty discouraged when i tried it in the past.

please forgive my ignorance in wireless internet with ubuntu.

---

### Post by fragos on 2006-09-24
If you run gnome-network-manager and then try wifi-radar, they will conflict.  I uninstalled gnome-network-manager and then wifi-radar worked.  Look in sessions to see if there is a gnome-nm in startup programs.  If so, disable it if you want to use wifi-radar -- my personal choice.

---

### Post by shanepardue on 2006-09-24
network-manager is neither installed or running when i try to connect to wifi-radar. could it be how i edited my interfaces config? or do i need to edit the wifi-radar config manually outside of the gui?

here's my interfaces config. tell me if it's corrupted or something. thanks!

```
#auto lo
#iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#iface lo inet loopback

#iface wlan0 inet dhcp
#wireless-essid sweethome

#auto wlan0

#iface lo inet loopback
```

---

