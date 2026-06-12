---
title: "will boot magic 8 work with my friends mac?"
date: 2008-09-08
forum: Apple Hardware Users
---

### Post by duffy_ryan on 2008-09-08
My friend has a macbook pro; but she really needs to (for school reasons) be able to run some windows programs (mainly MATLAB if anyones familiar with it). I have a copy of windows XP and a copy of Boot Magic 8. Does anyone think this will work? Any input will be appreciated, thank you.

---

### Post by cyberdork33 on 2008-09-08
You don't need to boot magic. Just resize your OSX partition in Disk Utility and create a FAT32 (msdos) partition for Windows. Also, why don't you just use BootCamp? (that's what it is for).

---

### Post by duffy_ryan on 2008-09-08
she doesnt wanna spend the $130 for boot camp.

---

### Post by cyberdork33 on 2008-09-09
> **duffy_ryan said:**
> she doesnt wanna spend the $130 for boot camp.Well, to argue that, you pay for Leopard, Boot Camp just happens to be part of that...

I didn't realize you were working on Tiger (that does make a difference since certain tools are not available). What you need to do is shrink the OSX partition to leave enough space on the disc for Ubuntu. Before you do anything though BACKUP, BACKUP, BACKUP.

See this wiki page for iMacs (the section I link to is just about partitioning which is the same for all Macs)
[https://help.ubuntu.com/community/Intel_iMac#Basic](https://help.ubuntu.com/community/Intel_iMac#Basic) instructions

Basically, you have three options.
[LIST=1]
[*]Use Commandline Tools in Tiger (Can be dangerous if you are not careful)
[*]Use gparted (available on the Ubuntu LiveCD as 'partition editor')
[*]Reformat the entire computer, wiping out the current install of OSX with Disk Utility on the Restore DVD.
[/LIST]

---

