---
title: "regestry restore in vista 32 through 7.10"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by squee on 2007-11-19
reinstalled Vista from the disc as I was trying to set up a dual boot between Vista and ubuntu. That went fine (eventually) but then Windows wouldnt update and I got an error code. I searched google and found what looked like a reliable solution which included detailed instructions for editing the registry.

Naturally I backed it up first. Now whenever I boot vista through GRUB i get something along the lines of "Error code 13, "Invalid or unsupported executable format"" Or something like that. I have googled the error exactly but to no joy.

My only resort (without reinstalling Vista which will delete the GRUB and cause a lot of hassle to reinstall both vista and ubuntu) is to back up the reg files. As per the instruction I exported the files and now i have a .reg file.

I need to know where and with what files i can replace it with? I have to do this through Ubuntu Can anyone help me please?


The meat of my menu.lst (because I know its what people will look for) is this
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cd564829-2aa3-4cd7-9c22-ca26965110ee ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cd564829-2aa3-4cd7-9c22-ca26965110ee ro single
initrd		/boot/initrd.img-2.6.22-14-generic

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4

title		Windows Vista/Longhorn (loader)
root		(hd0,3)
savedefault
makeactive
chainloader	+1   
```

There could be something wrong in that either

---

### Post by bumanie on 2007-11-19
I may not be the right person to be able to correctly diagnose this, but it would also be helpful if you post the output of
fdisk -lu
this will likely be helpful to others who look at your thread.

---

### Post by mikewhatever on 2007-11-19
I do not believe you can restore Vista's registry through Ubuntu. Reinstalling GRUB is a minor hassle and does not require reinstallation of either Ubuntu or Vista.

---

### Post by squee on 2007-11-19
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b622b61

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2490    20000893+  83  Linux
/dev/sda2            2491        6407    31457280    7  HPFS/NTFS
/dev/sda3           18337       18458      979965   82  Linux swap / Solaris
/dev/sda4   *        6408       18336    95819692+  83  Linux

Partition table entries are not in disk order



I might try and just reinstall vista and then reinstall the Grub over it. I was hoping that there would be an easy CLI solution to the problem or that there was an error in my menu.lst. Can someone check that there isnt before I start? That could be causing my whole problem. 
Thanks,

---

### Post by bumanie on 2007-11-19
I am very new to this sort of thing, but the way I see it, it looks as though you have linux on your first partition and windows on your second partition. From what I know (which isn't much), windows is usually in the first partition. The second thing that looks unusual is that the boot flag is on your fourth partition. I think this is normally on the windows partiton, if the computer is et up in the standard way with windows on the first partition. I suspect having windows on the second partition may have something to do with the grub error message.
Was ubuntu on the computer, before you tried installing vista?

---

### Post by squee on 2007-11-19
The way i went about setting up my computer was all wrong and unplanned. I would format and start all over again from scratch but i have almost 50Gb of music on another partition and reripping all my cds is just not an option.

TBH i reinstalled both OS's so many times that i cant remember which was where first. It was a steep learning curve for me as usually i just work with ubuntu when its already installed and I dont have to worry about installing it etc.

---

### Post by bumanie on 2007-11-19
Do you have or could you borrow an external hard drive to save your music to? Alternatively (although a bit time consuming and painful) you could fit the music onto 11 dvd's. In fact for another time, when the unexpected happens, it is not a bad idea to have such things backed up in some way. May be this is the time to a back up of all your important data, just to be on the safe side. I personally back up onto two external devices and for very important things (usually nowhere as large as 50g), I have a friend keep it on their hdd. It is unlikely all 3 backups would get destroyed at once.

---

