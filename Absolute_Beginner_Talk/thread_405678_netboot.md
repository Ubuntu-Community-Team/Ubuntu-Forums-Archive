---
title: "netboot"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by 13ojo on 2007-04-10
hello all.

Im running a ubuntu 6.10 server (1.7GHZ, 512mbram, 200GB hard-drive). It's running LAMP, and other stuff i've been adding as i go along, torrentlux, SSH etc.
Now i have another pc, Penitum 3, 400MHZ, 128mbram, Geforce 4 MX440. I had some success running Geexbox on it.

However, the cd-rom, and HDD's in the Pentium 3, aren't very reliable. seems the IDE cables are buggered. And they are noisy. So i want to netboot it, using a floppy disc to boot the pc.

Figured what i want is etherboot. But all walkthroughs i have require me to setup a DHCP server on the linux server box. This is a problem, as i use DHCP from my router, and most pc's are static anyway. (3 are static, 3 are dynamic). So can i use there walkthroughs without installing DHCP?. What's going to happen?.

also, is there a limit to the size of a OS i can boot through the network?, like time/ ram wise? eg, to big a OS might fail?

---

### Post by 13ojo on 2007-04-12
To run GEEXBOX via ethernet.

STEP 1) install a dhcp server

```
sudo apt-get dhcp
```

here's a config file i used before, it would offer ip's to pc's from 50 to 60, and direct them in the way of the files to netboot. please note, half of the options are probably unrequired, however it worked when i had them in, though i have a router running aswell, and this only booted half of the pc's, some get ip from the router!.

/etc/dhcpd.conf

```
subnet 192.168.0.0 netmask 255.255.255.0 {
default-lease-time 600;
max-lease-time 7200;
option routers 192.168.0.1;
option broadcast-address 192.168.0.255;
option subnet-mask 255.255.255.0;
option ip-forwarding on;
range 192.168.0.50 192.168.0.60;
next-server 192.168.0.200;
filename "/GEEXBOX/boot/pxelinux.0";
}
```

restart DHCP

```
sudo /etc/init.d/dhcp restart
```

STEP 2) install tftp-hpa

```
sudo apt-get install tftp-hpa
```

this doesn't require any setup, NOTE: i found that on ubuntu 6.10 apt-geting it creates /var/lib/tftpboot/ which is where the tftp server dishes files out from.

STEP 3) download a GEEXBOX image/build it from sources.

make a directory to mount the .iso

```
sudo mkdir /media/virtualcdrom
```

mount the .iso

```
sudo mount -o loop /"IMAGE LOCATION" /media/virtualcdrom/
```

then cp files

```
sudo cp /media/virtualcdrom/GEEXBOX /var/lib/tftpboot/
```

STEP 4) edit the pxelinux config files

```
sudo nano /var/lib/tftpboot/GEEXBOX/boot/pxelinux.cfg/default
```

change the nfsroot to read

nfsroot="TFTP SERVER'S IP":/var/lib/tftpboot/GEEXBOX

STEP 5) SET UP NFS, this is a common linux thing, and i can't remember how the hell to do it, just make sure you share /var/lib/tftpboot/GEEXBOX in /etc/exports.

now boot your pc, it should load the GEEXBOX over the net :D, though it's tough to figure out.


ps. i haven't figured out how to make a 2 DHCP servers play nice with ETHERBOOT, if i do i'll post how, as such, unless you are only running the one DHCP server, it might be tricky :D. but there's a rough guide anyway. so whoever searches this can now be enlightened "D

---

