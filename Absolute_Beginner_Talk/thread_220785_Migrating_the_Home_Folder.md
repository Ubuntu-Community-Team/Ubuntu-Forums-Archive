---
title: "Migrating the Home Folder"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-07-22
Hello everyone,
I am a newly converted Linux noob, and have installed 6.06 on my new Acer notebook (without any problems).
I have another ubuntu loaded notebook, and i want to transfer my documents and settings (home folder) to the new machine..
How do i do this using a USB-drive?
Also, what about the programs i had installed using Synaptic package manager? How do i transfer those?
Thanks..

---

### Post by aysiu on 2006-07-22
You want to copy the /home directory or the /usr directory.

You can't just do a straight *cp* command, though.

Forget about all the partitioning stuff, but this should help you at least with the command: [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by steve.horsley on 2006-07-22
> **kitt said:**
> Hello everyone,
I am a newly converted Linux noob, and have installed 6.06 on my new Acer notebook (without any problems).
I have another ubuntu loaded notebook, and i want to transfer my documents and settings (home folder) to the new machine..
How do i do this using a USB-drive?

Just copy your home folder to the drive, like this:
**cp -a /home/kitt /media/usbdisk**
You need root priv to create a new folder in /home on the target machine, so you use:
**sudo cp -a /media/usbdisk/kitt /home**
> Also, what about the programs i had installed using Synaptic package manager? How do i transfer those?
Thanks..
Many of those scatter files around, and run configuration scripts after installing the files. Best is to install again using synaptic on the new machine. 

If you're worried about download times on a modem, you can possibly transfer the cached package files from /var/cache/apt/archives although I've never tried this.

---

### Post by kitt on 2006-07-22
> **steve.horsley said:**
> Just copy your home folder to the drive, like this:
**cp -a /home/kitt /media/usbdisk**
You need root priv to create a new folder in /home on the target machine, so you use:
**sudo cp -a /media/usbdisk/kitt /home**

Many of those scatter files around, and run configuration scripts after installing the files. Best is to install again using synaptic on the new machine. 

If you're worried about download times on a modem, you can possibly transfer the cached package files from /var/cache/apt/archives although I've never tried this.
Thanks a lot...will try that out now..
By the way, will the theme settings, browsing history, FF extensions etc. be transferred? And will they over-ride my current settings?

And the /var/cache/apt/archives tip is *very* useful for a guy like me who doesnt have high-speed internet acess..thanks a lot for it..

---

