---
title: "How do I check how much space available in HDD on Kubuntu?"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Saoshyant on 2006-11-11
Hi,

I'm wondering, how do I check for how much free space there is on Kubuntu?  Either graphically or through command line?

---

### Post by loclei on 2006-11-11
go to system > administration > system monitor >file systems

---

### Post by taurus on 2006-11-11
Open a terminal and type

```
df -h
```

---

### Post by Saoshyant on 2006-11-11
Thank you.

It wasn't very obvious.  I'd expect to find an option to check for free space on media:/ but this is life for you.  Thanks again.

---

### Post by loclei on 2006-11-11
the df -h command does just that

it shows more info than going to file systems in system monitor 
just look
```

Filesystem            Size Used Avail Use% Mounted on
/dev/hda6             6.3G  2.3G  3.8G  38% /
varrun                252M   52K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  120K  9.9M   2% /proc/bus/usb
udev                   10M  120K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/hda1             3.0G  2.1G  841M  72% /media/windows
/dev/hda5              28G   23G  5.5G  81% /media/hda5

```

---

### Post by elcasey on 2006-11-11
The [FONT="Courier New"]-h[/FONT] switch stands for "Human Readable," Saoshyant. If you just type [FONT="Courier New"]df[/FONT] you'll get a string of numbers showing space down to the last bit.

---

### Post by mdsmedia on 2006-11-11
> **Saoshyant said:**
> Thank you.

It wasn't very obvious.  I'd expect to find an option to check for free space on media:/ but this is life for you.  Thanks again.In Gnome (Ubuntu), in the file manager Nautilus, you can see free space available in any drive at the bottom of the file manager window. I'd imagine you can do the same in the file manager in KDE (Kubuntu), but not having used Kubuntu to any great extent I'm not sure.

---

