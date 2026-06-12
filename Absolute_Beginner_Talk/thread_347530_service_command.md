---
title: "service command"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by tnthomas17 on 2007-01-27
How can I access the service command in ubuntu as it's not recognized when I put it in, I need to release and renew my IP address for my wlan card.

---

### Post by xopher on 2007-01-27
a simple solution would be: ```
sudo ifdown -a; sudo ifup -a
```

---

### Post by tnthomas17 on 2007-01-27
tried that, but it does not seem to work very well, I keep getting no DHCP offers or something like that, when i've entered a valid ESSID for a network that is within range

---

### Post by steve.horsley on 2007-01-28
I would use **sudo dhclient eth0** personally.

---

### Post by az on 2007-01-28
> **steve.horsley said:**
> I would use **sudo dhclient eth0** personally.

sudo ifdown eth0
sudo ifup eth0 
will take advantage of any ubunutu-specific scripts that your wireless device may use.

Using dhclient will not.

---

### Post by Delkster on 2007-01-28
> **tnthomas17 said:**
> How can I access the service command in ubuntu as it's not recognized when I put it in, I need to release and renew my IP address for my wlan card.

There's no `service' command in Ubuntu (as far as I know, it's a Red Hat thing). You can start, stop and restart services, or daemons, through the scripts in /etc/init.d. For example, to tear down and reinitialize the network you could use "sudo /etc/init.d/networking restart". You could also just go to the graphical network configuration tool and disable and then re-enable the corresponding network interface. That would renew the IP address for that interface.

---

### Post by tnthomas17 on 2007-01-30
I'll try the script one, because ifup and ifdown weren't working...

thanks

---

