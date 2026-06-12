---
title: "upgrade to Karmic no boot eth1 craziness"
date: 2009-11-05
forum: Apple Hardware Users
---

### Post by ubuntubrian on 2009-11-05
I upgraded the ol' TiBook PPC to Karmic as the Jaunty upgrade had worked so well. The upgrade ran fine and after restarting and the splash screen coming up I thought I was shiny. 
But no,
changing to a console during booting seems normal until detecting my airport card and that even seems fine but then I get endless lines of ip addresses and eth1 connecting and disconnecting. No log-in screen and the lines just scroll faster and faster.
How can I disable this when booting up? How can I fix it?
I see no errors but once the airport card is detected and all seems well this is what happens....


Thanks

---

### Post by ubuntubrian on 2010-01-21
Bump?

---

### Post by linuxopjemac on 2010-01-22
you night want to start from a liveCD and chroot into your system and then empty the /etc/network/interfaces file. Maybe it tries to set an ip address but something is wrong with the airport module. To chroot into the environment from the liveCD:

```
sudo mkdir /mnt/root
sudo mount -t ext4 /dev/sda4 /mnt/root (if your filesystem is ext4, could be ext3 as you upgraded from jaunty)
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
```

and then go to /etc/network/ and edit
```
sudo nano /etc/network/interfaces
```

and then you empty the whole file and save. It won't try to setup the network while booting then.

What you can also do is to blacklist the module which is responsible for airport, which is either bcm43xx or b43. You can add them to the blacklist file:

```
sudo nano /etc/modprobe.d/blacklist
```

and add

```
bcm43xx
b43
bcmwl
```

at the end.
sudo nano /etc/network/interfaces[/CODE]

You can then try to have a look at the airport stuff later.

---

### Post by ubuntubrian on 2010-01-22
Thanks so much for the info! I dual boot the TiBook with OS X and so I just booted up that and then sudo'ed into the network/interfaces and moved it out of the way and booted into Karmic. Boot went fine and had no network, of course. I had some old files in there and i renamed the latest old one to "interfaces" and rebooted. I'm writing this reply from Karmic on my TiBook!

Thanks again.

BTW, I have no idea why the old interfaces works.there are some added interfaces from when I was out of the country and had to add some but the standard stuff was the same as the new file that was created.

---

