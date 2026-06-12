---
title: "Computer sometime hangs on bootup"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by baph0m3t on 2008-01-29
Hi, I'm a complete beginner to linux and ubuntu. Everything is awesome but sometimes on boot up the computer hangs and i have to manually power down my comp and try again. Anybody know what I can possibly do to fix this?

---

### Post by brokenhachi on 2008-01-29
She?

---

### Post by baph0m3t on 2008-01-29
> **brokenhachi said:**
> She?

lol sorry i hit enter on accident

---

### Post by baph0m3t on 2008-01-30
Anybody have any ideas?

---

### Post by cartisdm on 2008-01-30
How long has it been up and running?  A simple fix, could be to just reinstall.  I would recommend that unless you went through a lengthy process to get it installed in the first place.

---

### Post by baph0m3t on 2008-01-30
> **cartisdm said:**
> How long has it been up and running?  A simple fix, could be to just reinstall.  I would recommend that unless you went through a lengthy process to get it installed in the first place.

Well I hadn't had it up for long, so I said what the heck and did a resintall. I downloaded the alternate installer instead of the Live CD version, checked the hash (it matched) and burned the image at 4x speed. 

Reintalled.

Still having the problem of it hanging on boot up. :( Anybody else? This is frustrating because somtimes I have to hard reboot a couple times before it loads. It gets to the progress bar screen and just a sliver of orange shows, and it never goes anywhere...

:(

---

### Post by baph0m3t on 2008-01-30
Ok, I implemented this fix... however it is too early for me to tell if this has fully worked. I'll repost if I run into problems or if it seems to have been resolved at a later time after I have rebooted enough to feel confident it worked. Anyway, here's what google found:

You have to edit the menu.lst file. Load up the terminal and type:

1. backup menu.lst:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup

2. edit menu.lst:
sudo gedit /boot/grub/menu.lst

You just need to ad `irqpoll` to your grub line. So in /boot/grub/menu.lst I added irqpoll to the kernel line: kernel /boot/vmlinuz-2.6.20-15-generic (add irqpoll after quiet splash)

Then saved the menu.lst file and I was done.

Hope this is a final solution.

Sources:

[http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/](http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/)

[http://www.fak3r.com/2007/06/22/failed-to-set-xfermode-solved/](http://www.fak3r.com/2007/06/22/failed-to-set-xfermode-solved/)

---

