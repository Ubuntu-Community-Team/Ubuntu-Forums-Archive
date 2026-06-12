---
title: "Networking problem"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-07
i recently installed ubuntu 7.04 .I am currently dual-booting it with XP.Though i can access the net(ethernet) via XP ,whenever i open my ubuntu dektop since the last day or so then it shows searching IP address and the network link rotates anf finally shows the computer server which and a ballon shows ensuring connectivity yet i don't have my net as i can't view pages.

---

### Post by gerscht on 2007-06-07
I suppose you're behind a router and are getting the IP address via DHCP from the router.
Have you tried setting the IP address manually to the same as in your windows installation?
there might be something wrong with your network manager...

---

### Post by pardesi on 2007-06-07
how do i get the IP address and how do iset it manually in the ubuntu

---

### Post by gerscht on 2007-06-07
you can see it via ```
ifconfig
```
and either set it via the network manager (Manual configuration) or edit the settings in /etc/network/interfaces
```
sudo gedit /etc/network/interfaces
```
It should look something like this for DHCP
```

iface eth0 inet dhcp 
auto eth0

```
And like this for static configuration
```

auto eth0
iface eth0 inet static
    address 192.168.1.1
    netmask 255.255.255

```
you can restart your network by 
```

sudo /etc/init.d/networking restart

```

---

### Post by pardesi on 2007-06-07
the following code 
```
sudo gedit/etc/network/interfaces
```
gives me a plank page in GEdit.
i tried this
```
/etc/hosts
```
whih then showed 
```
Permission denied
```
i have DHCP

---

### Post by gerscht on 2007-06-07
did you have a space between gedit and /etc like:
```

sudo gedit /etc/network/interfaces

```
if so, than it's quite wired that you don't have an interfaces file. But this is the reason why it doesn't work (what does ifconfig say?)
create a new file  and paste this:
```

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

```
This will bring back your loopback device and eth0 (don't forget to restart the network, see above)
I hope this helps

BTW: the hosts file doesn't have anything (or at least not that much) to do with this, it's for resolving names to IP's, not for obtaining an IP

---

### Post by pardesi on 2007-06-07
when i used the following code 
```
cat etc/network/interfaces
```
i get 
```
auto lo
iface loinet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```
this may help you helping me.
even after the space i got a blank Gedit document .should i save it sfter the changes.
though i do have an interface file it's blank

---

### Post by pardesi on 2007-06-07
my interface now gives the same answer as the code above[B]
see next post[/B]

---

### Post by pardesi on 2007-06-07
my interface now gives the same answer as the code above 
```
auto lo
iface loinet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by pardesi on 2007-06-07
here is what if config says.
i have added it as an open office attachment.see below for attachment

---

### Post by pardesi on 2007-06-07
attachment

---

### Post by gerscht on 2007-06-07
ok, it didn't get an IP via DHCP.
What IP address do you have when you're in windows ?
Write it down and set it static in ubuntu (see above).
Don't forget to restart your network via 
```

sudo /etc/init.d/networking restart
```
after changes, otherwise changes will available after a reboot only.

---

### Post by pardesi on 2007-06-07
where do i set it static .in the interfaces or somewhere else .whose IP address should i ude ?

---

### Post by Sethalos on 2007-06-07
To find your IP in Windows you can simply click on the Start Button - Run - Type CMD, press ok...when the command window comes in type ipconfig.

Use the ip address there in Ubuntu as explained above. Might need the Default gateway as well.

---

### Post by pardesi on 2007-06-08
i went to the network interfaves and changed DHCP to static.
also i tried changing network manager config from DHCP to static.but all in vain.also if i use my ubuntu first and restart with windiws my win shows low connecticvity though it connects if i start ir after shutting down.
also if this can help you that my network cinnection shows i have local connection though i have ethernet this may help you helpng me....

---

