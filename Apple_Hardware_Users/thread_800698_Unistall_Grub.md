---
title: "Unistall Grub"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by bozzochet on 2008-05-20
Hello,
I have a double boot Kubuntu+MacOsX and I use rEFIt and Grub. Few time ago I made, making an error, ```
sudo grub-install /dev/sda4
``` instead of ```
sudo grub-install /dev/sda
``` so I installed grub also in the Linux partition. Now when I boot my MacBook rEFIt shows to me TWO penguins logo for booting linux, besides of the other normal logos... Each of the TWO penguins (boot from HD and boot from Partition4) are valid and load grub correctly but however I qould like to remove one of the two.
Someone does know how to unistall grub?
Thanks

---

### Post by cyberdork33 on 2008-05-20
there are a few methods here:
[http://www.slax.org/forum.php?action=view&parentID=9415](http://www.slax.org/forum.php?action=view&parentID=9415)

I think this tool might work for you too:
[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

---

### Post by bozzochet on 2008-05-20
Now I try...

I didn't think to fixmbr & co because I tought that it was able to "erase" grub only from the first volume of the disk and that on an Apple it was unable aslo to do it...

Thanks

---

### Post by volanin on 2008-05-20
If your sda4 partition is EXT2 or EXT3:

```
sudo dd if=/dev/zero of=/dev/sda4 bs=512 count=1
```

Don't get the numbers wrong, or your partition will be destroyed.
Enjoy!
:)

---

### Post by cyberdork33 on 2008-05-20
It is preferred to remove it from the MBR but that will work too!

---

### Post by bozzochet on 2008-05-21
Sorry but I didn't understand well...

The methods you said to me are all (as I understood) for the whole disk...
I have grub installed partitions (I said only the sda4 of sda but I have also in sda5 that is a FAT32 partition...) and refit at the startup ask to me from which of these 3 partition I want to boot; Obviously every of these 3 is working correctly...

---

### Post by bozzochet on 2008-05-21
I tried to istall lilo on the partitions I'm talking about and than unistall it trough its command ```
lilo -u /dev/sdaX
```.
On the boot refit doesn't show me the penguin of linux but the symbol of windows (the 4 squares) saying to me 'Boot Legacy from' ... and if I choose it I've this symbols on the screen without any other event...
But I want to remove the symbol itself!!! I want only 1 penguin for Linux, the apple for MacOSX, the symbol for the Apple Hardware Test and below the other 4 icons smaller...

---

### Post by cyberdork33 on 2008-05-21
volanin's method just writes zeros to the bootsector of the MBR. You should use it on sda5

---

### Post by bozzochet on 2008-05-21
yes but he said that it works only on ext2/ext3 partitions... I have FAT32 partition...

---

