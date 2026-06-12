---
title: "how to save current config"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Mightygringo on 2008-01-16
I want to save my current background and network settings what would i have to do to do this?

---

### Post by njparton on 2008-01-16
Are you just running the live CD or have you installed to a hard drive?

You can't do anything if the former, and you need do nothing if the latter.

---

### Post by milosz.galazka on 2008-01-16
Look at */etc/network/interfaces* file and *man interfaces* manual.
Maybe it is what you are searching for.

---

### Post by Mightygringo on 2008-01-16
I got it installed but every time i reboot and type in ifconfig "eth1"  goes to eth2 then i reboot again eth3 and most times i cant make it online cuz i dont know very muck about linux can u help me make my current setting perment or at least alter a .config so it will keep the same settings

---

### Post by njparton on 2008-01-17
That's because the mac address of your nic is changing each time you boot up. It's a driver issue.  The last 3 octets of a mac address can be changed locally, the first few sets are hardwired.

Add the following line to your /etc/network/interfaces file under the appropriate ehtA section:

```

hwaddress ether XX:XX:XX:XX:XX:XX

```

where XX:XX:XX:XX:XX:XX is the mac address you want to use.

Reboot.

It should then stay as ethA after every reboot (where ethA is the lastest eth3, eth4 etc assignment).

You could also change eth3 or eth4 back to eth0 and reboot.

---

### Post by Mightygringo on 2008-01-19
auto lo
iface lo inet loopback


iface eth1 inet dhcp



auto eth1

iface eth2 inet dhcp

auto eth2

iface eth4 inet dhcp



auto eth4

iface eth8 inet dhcp

auto eth8

iface eth9 inet dhcp





auto eth9

iface eth12 inet dhcp

auto eth12
 thats what my network interface says where do i add that command?

---

### Post by njparton on 2008-01-19
First find the mac address under administration > network tools > eth12 (or whatever number it's currently using).

Then replace everything in your /etc/network/interfaces file with the following:

```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
hwaddress ether XX:XX:XX:XX:XX:XX
auto eth0

```

where XX:XX:XX:XX:XX:XX is the mac address you found.

Reboot or 

```

sudo /etc/init.d/networking restart

```

You'll then have a connection at eth0 that will stay there.

---

