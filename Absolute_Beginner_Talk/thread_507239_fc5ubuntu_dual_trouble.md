---
title: "fc5/ubuntu dual trouble"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by sulblk27 on 2007-07-22
Hello all, I must first apologize because I erroneously posted in the Cafe' forum, with this post (moderators please forgive this silly mistake)I have searched this forum, and others since yesterday...all things that I have tried have been in vain. Keeping in mind, I just installed this distro last night so if a reinstall is necessary I will not mind. There are other issues...like the no shutdown, but this one is more important to me. Boots to ubuntu just fine...trying fc5 is a hold nother ball of wax. I have posted the fdisk and menu.lst, any assistance will be greatly appreciated.

Disk /dev/hda: 13.6 GB, 13613064192 bytes
255 heads, 63 sectors/track, 1655 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 13 104391 83 Linux
/dev/hda2 14 1655 13189365 8e Linux LVM

Disk /dev/hdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 1 248 1992028+ b W95 FAT32
/dev/hdb2 * 249 757 4088542+ 83 Linux
/dev/hdb3 758 784 216877+ 5 Extended
/dev/hdb5 758 784 216846 82 Linux swap / Solaris

## ## End Default Options ##

title Ubuntu, kernel 2.6.17-12-Lion
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-12-generic root=/dev/hdb2 ro quiet splash
initrd /boot/initrd.img-2.6.17-12-generic
quiet
boot

title Ubuntu, kernel 2.6.17-12-Lion (recovery mode)
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-12-generic root=/dev/hdb2 ro single
initrd /boot/initrd.img-2.6.17-12-generic
boot

#title Ubuntu, kernel 2.6.17-10-generic
#root (hd1,1)
#kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro quiet splash
#initrd /boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
#root (hd1,1)
#kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro single
#initrd /boot/initrd.img-2.6.17-10-generic
#boot

title Ubuntu, memtest86+
root (hd1,1)
kernel /boot/memtest86+.bin
quiet
boot

title Fedora Core 5
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-1.2320.fc5 root=/dev/hda1 ro quiet splash
initrd /boot/initrd-2.6.20-1.2319.fc5.img
quiet
boot

I have tried moving FC5 to the top, using chainloader +1, and a variety of other options I have found. The most I can get with the current system is file no found. Another way, starts the boot for fc5 then kernel panic (sort the state I'm in now!)....one of the other errors mount: could not find filesystem '/dev/root' and unable to access resume device (/dev/VolGroup01/LogVol01) when I have LogVol00. Anyway...thank you for reading thru this post in order to try and assist a noobie in times of need.

---

### Post by confused57 on 2007-07-22
Try using a configfile entry to boot Fedora:
```
title        Fedora
configfile   (hd0,0)/boot/grub/menu.lst
```

The "Absolute Beginner Section" is the best section to post for getting a solution for any problems you have, the "Cafe" is for general BS and discussions on various & sundry linux/Ubuntu topics, it's not really the place to ask for help.  Don't worry about posting there, you didn't know, and they were probably just politely directing you here.

---

### Post by sulblk27 on 2007-07-22
Thank you so much for the reply and kind words...I am trying that code now....there are only the two lines?  no intrid, kernel or boot?
Came back File not found....I appreciate the reply and assist...I'll keep at it till my eyes pop out tonight, then try again in the am...

---

### Post by confused57 on 2007-07-22
> **sulblk27 said:**
> Thank you so much for the reply and kind words...I am trying that code now....there are only the two lines?  no intrid, kernel or boot?
Came back File not found....I appreciate the reply and assist...I'll keep at it till my eyes pop out tonight, then try again in the am...
Fedora may use grub.conf, instead of menu.lst, then this entry should work:
```
title        Fedora
configfile   (hd0,0)/boot/grub/grub.conf
```

This explains quite well how configfile, chainloading, & symlinking work to boot other distros:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by sulblk27 on 2007-07-23
After having someone go over the entry he noted two different numbers in my kernel and initrd entries
kernel /boot/vmlinuz-2.6.20-1.[COLOR="Red"]2320[/COLOR].fc5 root=/dev/hda1 ro quiet splash
initrd /boot/initrd-2.6.20-1.[COLOR="Red"]2319[/COLOR].fc5.img
Once that was changed I'm able to boot iinto fc5......Thank you confused57, for your assistance and I will check out the links...more knowledge the better...one issue down, now onto the minor ones....:guitar:
The whole entry is
title Fedora Core 5
root (hd0,0)
kernel  /vmlinuz-2.6.20-1.2320.fc5 ro root=/dev/VolGroup01/LogVol00 rhgb quiet 
initrd   /initrd-2.6.20-1.2320.fc5.img
savedefault
boot

---

