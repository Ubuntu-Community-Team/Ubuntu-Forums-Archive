---
title: "Manual installs on Debian Squeeze"
date: 2011-07-15
forum: Any Other OS
---

### Post by r3bol on 2011-07-15
Hi, I've just installed debian-6.0.2.1-i386-netinst.iso (Debian Squeeze)

I have a working terminal, but no ethernet internet connection. I can connect to the internet, but only through an open hotspot from my neighbour (which is totally legal in my country ;)). Problem is, I think I have to install something called wireless-tools to use wifi and I've never done manual installs before. 

What would I need to do or what would I have to read in order to do a manual install like this?

Thanks in advance.

---

### Post by Zill on 2011-07-15
> **r3bol said:**
> Hi, I've just installed debian-6.0.2.1-i386-netinst.iso (Debian Squeeze)...
Debian is a wonderful OS but it is not quite as user-friendly as Ubuntu or Mint and you may need to do more web-research to resolve problems.

As this forum is primarily for Ubuntu, I suggest you may get more relevant assistance directly from the [Debian forums]("http://forums.debian.net").

---

### Post by mips on 2011-07-15
What wireless chipset are you using?

---

### Post by r3bol on 2011-07-15
> **mips said:**
> What wireless chipset are you using?
It's an Atheros for the eeePC 4G. I tried the wicd, wicd-cli and wicd-client commands, but the terminal returned Command not found.

Just registering with the Debian folks now ;)

---

### Post by mips on 2011-07-15
> **r3bol said:**
> It's an Atheros for the eeePC 4G. I tried the wicd, wicd-cli and wicd-client commands, but the terminal returned Command not found.


Did you actually install those packages?

---

### Post by r3bol on 2011-07-15
> **mips said:**
> Did you actually install those packages?
Nope, I'm not on the net so I can't apt-get them. I'm wondering which ones I need and what would be the easiest way to manually install them?

---

### Post by mips on 2011-07-15
> **r3bol said:**
> Nope, I'm not on the net so I can't apt-get them. I'm wondering which ones I need and what would be the easiest way to manually install them?

I would just connect via a wire connection in order to get the wireless going.

---

### Post by snowpine on 2011-07-15
Wired ethernet connection is easiest; if that's not an option then don't use the "netinstall" CD; use "CD 1" and you'll get a basic desktop with networking, etc.

---

### Post by NightwishFan on 2011-07-16
No CD1 does not include network-manager. Try the live dvd/usb. It is only 1.1gb and has a full Gnome Desktop.
[http://www.debian.org/CD/live/](http://www.debian.org/CD/live/)

Setting up wifi via the terminal is annoying but possible if the wifi is not encrypted. I am not sure if the netinstall has wifi tools but if it does..

Log in as root (or use sudo if you set that up)
```
ifconfig wlan0 up
```
```
iwconfig wlan0 essid NAMEOFNETWORK
```
```
dhclient wlan0
```

Should do it. Replace NAMEOFNETWORK with the name of the unencrypted wifi you are trying to connect to.

If this works edit your sources with:
```
nano /etc/apt/sources.list
```

If you are running Debian 6 at least have this line (might already be pre set up)
```
deb http://ftp.us.debian.org/debian squeeze main contrib non-free
```

Finally run this and then you can apt-get install whatever you want.
```
apt-get update
```

---

### Post by r3bol on 2011-07-16
> **NightwishFan said:**
> 
```
ifconfig wlan0 up
```
```
iwconfig wlan0 essid BUFFALO
```
```
dhclient wlan0
```

Thanks for the suggestion, running the last command, I get...
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory

Hmmm... interesting because /etc/resolv.conf does reside in /etc/ and I was su when typing the command.

But I could just find a place to hook it up and install the components I need.

---

### Post by NightwishFan on 2011-07-16
I have seen that message before, I think it is normal.

---

### Post by r3bol on 2011-07-16
You're right! I tried wget and connected to google. Looks like I'm online. Kiitos NightWish Fan ;)

---

### Post by NightwishFan on 2011-07-16
> **r3bol said:**
> You're right! I tried wget and connected to google. Looks like I'm online. Kiitos NightWish Fan ;)

Ole hyvä (i think) Enjoy! :)

---

### Post by r3bol on 2011-07-16
> **NightwishFan said:**
> Ole hyvä (i think) Enjoy! :)

OMG how rude! Just kidding, it's correct :D

---

