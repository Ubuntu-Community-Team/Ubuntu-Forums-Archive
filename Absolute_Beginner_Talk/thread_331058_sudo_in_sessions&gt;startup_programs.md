---
title: "sudo in sessions&gt;startup programs"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by zmuth734 on 2007-01-04
Is it possible to use sudo in a startup program command?

I want to use ```
sudo iwpriv eth1 set_mode 2
```

I'm asking this because usually the first time I use sudo it asks for my password.

Thanks for your help.

---

### Post by kerry_s on 2007-01-04
Put it in init.d to have it start at boot.In terminal->

sudo gedit /etc/init.d/eth1

put this in it->

#!/bin/sh
iwpriv eth1 set_mode 2


Now save & make it executable->

sudo chmod +x /etc/init.d/eth1


Congratulations you just made your first startup script. :)

---

### Post by zmuth734 on 2007-01-04
> **kerry_s said:**
> Put it in init.d to have it start at boot.In terminal->

sudo gedit /etc/init.d/eth1

put this in it->

#!/bin/sh
iwpriv eth1 set_mode 2


Now save & make it executable->

sudo chmod +x /etc/init.d/eth1


Congratulations you just made your first startup script. :)

Hey thanks for helping me, I followed exactly what you said and to test it I first set_mode to 6 in the terminal then restarted and it was still 6 after the reboot :???:

---

### Post by Ecthelion on 2007-01-04
[QUOTE=David_T]To add a script that runs at startup, just add whatever you want to /etc/rc.local.
That's what I do for loading my iptables settings and it works great.

(edit: btw you don't have to use sudo in rc.local, it will be run as root)[/QUOTE]
[SIZE="1"]Found [here]("http://ubuntuforums.org/showthread.php?t=286958&highlight=startup+script")[/SIZE]

Maybe this works for you too...

---

### Post by zmuth734 on 2007-01-04
> **Ecthelion said:**
> [SIZE="1"]Found [here]("http://ubuntuforums.org/showthread.php?t=286958&highlight=startup+script")[/SIZE]

Maybe this works for you too...

Thanks, works

---

### Post by kerry_s on 2007-01-05
> **zmuth734 said:**
> Hey thanks for helping me, I followed exactly what you said and to test it I first set_mode to 6 in the terminal then restarted and it was still 6 after the reboot :???:

Woops, sorry about that i for got a step to put it into the run levels. suppose to be this->

sudo gedit /etc/init.d/eth1

put this in it->

#!/bin/sh
iwpriv eth1 set_mode 2


Now save & make it executable->
run in terminal->

sudo chmod +x /etc/init.d/eth1

sudo update-rc.d eth1 start defaults

---

