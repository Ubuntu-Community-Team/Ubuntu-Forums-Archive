---
title: "wondering about mutiple disk running"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by bryan_M23 on 2007-05-07
hi. i just got Ubuntu today, and i am very pleased with the operating system! however, someone else in my house hold isnt so pleased. they want to continue using windows XP. what i did was disconnected the existing hard drive to keep all of its data on it, and connected a spare i had lying around. i installed Ubuntu to that and it worked fine but, since both disks are set to master, when i tried connecting them both, the whole system froze. so now i have the pain of whenever i come on i have to open up the case, disconnect the other hard drive, reconnect my hard drive, and boot up, and put it all back to normal when I'm finished. Does anyone know some other way that i could switch between hard disks? Switching all the time can not be good for my connectors.

---

### Post by seetho on 2007-05-07
You can get one of those removable harddrive things for your PC.  I used it a while back but found that they don't last very long, but they are cheap ~ <$10.

Alternatively you can connect both as Master-Slave then configure your PC to dual boot.  There are lot of threads on this forum with instructions how to do this.  Sometimes they can be a little complicated if you are new.

Easiest would be to back up all your data first (just in case) to external HDD or CD/DVD, connect you Win HD as master, connect ubuntu disk as slave, then do fresh install of ubuntu.  You should get dual boot system after that.  It doesn't take so long to do a fresh install of ubuntu so it's almost not worth the time fiddling about the partitions, and grub and mbrs.

---

### Post by confused57 on 2007-05-07
See this guide:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

You should be able to connect your Window's hard drive as slave, make sure jumper settings are correct on the hard drive, or if you're using cable select, that should be fine & jumper shouldn't need any adjustment.

---

### Post by forsaken_pariah on 2007-05-07
I had a similar problem but I found that for some reason Windows never seems to work right unless it's on the master drive.

---

### Post by alienexplorers on 2007-05-07
I too have had a problem trying to run Windows on a slave drive.  I ended up making the Windows drive the Master and Ubuntu the slave.  I have grub loaded on the MBR and use it to dual boot between the two Operating Systems.

---

