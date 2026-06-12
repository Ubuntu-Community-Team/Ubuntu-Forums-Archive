---
title: "Wi-Fi Not Working On Ubuntu 13.10 MacBook Pro"
date: 2014-03-21
forum: Apple Hardware Users
---

### Post by sps828gaming on 2014-03-21
Hi Everyone!

I'm new to Ubuntu and I decided to install 13.10 64bit on my mid-2010 MacBook Pro and since I installed it I haven't been able to connect to a wifi network. I tried installing Ubuntu on a Windows PC but the wifi didn't work on that because of the network card. If my wifi problem is because of the network card than I can't replace it since it's built in so does anyone know how to fix the wifi?

Thanks

---

### Post by varunendra on 2014-03-21
Welcome to Ubuntu Forums! :)

To let us see your wireless card and the driver in use (if any), please open a terminal (Ctrl-Alt-T) and post back the output of -
```
lspci -nnk | grep -iA2 net
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by sps828gaming on 2014-03-21
After typing in

```

lspci -nnk

```

I scrolled down to where it said about the network card and it said:
```

02:00.0 Network controller [0280]: Broadco, Corporation BCM4322 802.11a/b/g/n Wi
reless LAN Controller [14e4:432b] (rev 01)
          Subsystem: Apple Inc. AirPort Extreme [106b:008d]
          Kernal driver in use: b43-pci-bridge

```
I also get nothing when typing in:
```

grep -iA2 net

```

After typing in the second command I get a window when I try to close Terminal saying:
```

Close this terminal?

There is still a process running in this terminal. Closing the terminal will kill it.

```

---

### Post by bapoumba on 2014-03-21
Thread moved to Apple Users.

---

### Post by varunendra on 2014-03-21
> **sps828gaming said:**
> After typing in the second command I get a window when I try to close Terminal saying...

That was actually a single command, the output of the first command being "Piped" (|) to the second one as input, to filter out unwanted lines. But anyway, I got what I wanted -
```
02:00.0 Network controller [0280]: Broadco, Corporation BCM4322 802.11a/b/g/n Wi
reless LAN Controller [14e4:432b] (rev 01)
          Subsystem: Apple Inc. AirPort Extreme [106b:008d]
          Kernal driver in use: b43-pci-bridge
```

With a wired connection, please try -
```
sudo apt-get install linux-firmware-nonfree
```
Followed by either a reboot, or -
```
sudo modprobe -rv b43
sudo modprobe -v b43
```
Does the wifi work now?

If you don't have a wired connection or other means to connect to internet, manually download the firmware package from this link : [http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

*[COLOR="#800000"](**EDIT :** Corrected the above link)[/COLOR]*

Copy the downloaded .deb package to your Ubuntu Desktop, open a terminal, and run the following command to manually install it -
```
sudo dpkg -i Desktop/linux-firmware*.deb
```
Followed by a reboot or the commands as above.

If that doesn't make your wifi work, we may have to try the proprietary STA driver, but for now, please try this and report back how it goes.

---

### Post by sps828gaming on 2014-03-21
When I tried:
```

sudo apt-get linux-firmware-nonfree

```
I got:
```

E: Unable to locate package linux-firmware-nonfree

```
When I tried to manually download it the link you sent me was dead.

---

### Post by varunendra on 2014-03-21
> **sps828gaming said:**
> When I tried to manually download it the link you sent me was dead.

Sorry, a copy-paste mistake on the link. I've corrected the link, please use that one, or choose another mirror of your choice from the main download page : [http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download)

---

