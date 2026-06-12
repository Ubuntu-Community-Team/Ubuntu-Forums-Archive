---
title: "installing ubuntu on a second IDE drive"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by moisea on 2007-11-23
hello, i have a ubuntu cd that i want to install  on my second HDD . however, seems that it only sees my primary SATA  HDD with xp Os and not the Secondary IDE HDD, which i want to use for linux.when its time to partition it only shows the SATA drive not the IDE, even though it is on my  bios and computer.
can someone please help me on how to install ubuntu on my second drive?
many thanks.

---

### Post by LaRoza on 2007-11-23
I would disconnect the SATA drive for this.

I have heard of issues when mixing SATA and PATA, and don't remember the fix.

---

### Post by moisea on 2007-11-23
thanks LaRosa but i would like to be able to switch to and from XP when i need to without having to keep plug in and unplugging the SATA hard drive. unless this is a one off.
many thanks.

---

### Post by mahiyar on 2007-11-23
I have exactly the same configuration one ide one sata, windows + 2 linux on ide, 2 linux on sata. However booting from sata. The process is a bit complicated and involved.
1)As LaRoza suggested when installing Ubuntu remove the SATA, make boot from ide install ubuntu, and put the boot loader in the MBR of ide.
2)Reattach SATA (with windows) from BIOS keep the first boot disc as IDE.
3)On starting the boot will take you to Ubuntu bypassing windows, however change the menu.lst to chainload windows.
4)If all is ok you will see the windows option in the grub which will work .

The best advice is to thoroughly read this wonderfully written page to understand what u are doing [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by LaRoza on 2007-11-23
I meant disconnect it for the install. Reconnect it after.


After installing and reconnecting both drives, 

Post the results of 
```

cat /boot/grub/menu.lst

```

and

```

sudo fdisk -l

```

and tell us what other OS you have and I or others will add any other OS to it for you.

---

