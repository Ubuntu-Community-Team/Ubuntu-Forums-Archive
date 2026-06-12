---
title: "Is it Possible to copy with dd the Grub in the MBR ? (Before-installing-Windows)"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-02-19
Hi, 

Like a dd: 
```
dd if=/dev/hda of=/boot/boot.MBR bs=512 count=1
```
  
Thx

Patrick

---

### Post by Herman on 2006-02-19
Hello Patrick, in the first sector (512 bytes), there is also the 2 byte magic number and the 64 byte partition table, so if you only want the part with the IPL for the bootloader then (512 -2 -64 =446)  
```
sudo dd if=/dev/hda of=/home/herman/MBR.image bs=446 count=1
```What do you think? I'm not sure about which one is best, but this is the one I've got. I have not tested it as yet, so I cannot say if it is right or wrong, it's something I found by reading.
Maybe tomorro I will try them both out and compare.   :-D (Herman)

---

### Post by steve.horsley on 2006-02-19
I have often taken a shot of the boot partition exactly that way. I have even had occasion to replace it. It works.

The problem is that if installing windows changes the partition table, than you cannot afford to put the whole sector back again. I would be inclined to capture the entire 255 bytes to file, but then as herman says, just put the frist 244 bytes of that back to rep[lace the bootloader after windows has overwritten it. 
```
sudo dd if=/boot/MBR-b4-win.image of=/dev/hda bs=446 count=1
```

---

### Post by patrick295767 on 2006-02-20
[QUOTE=steve.horsley]I have often taken a shot of the boot partition exactly that way. I have even had occasion to replace it. It works.

The problem is that if installing windows changes the partition table, than you cannot afford to put the whole sector back again. I would be inclined to capture the entire 255 bytes to file, but then as herman says, just put the frist 244 bytes of that back to rep[lace the bootloader after windows has overwritten it. 
```
sudo dd if=/boot/MBR-b4-win.image of=/dev/hda bs=446 count=1
```[/QUOTE]
  
Thank you very much of your information !!
  
Then, this looks pretty handy to restore the Grub after Windows Install.
 I am gonna try this.

Thx

Greetings,

Patrick

---

### Post by Herman on 2006-02-21
Here's something interesting, try this:```
sudo dd if=/dev/hda1 of=mbr.img bs=512 count=1
``````
od -Ad -tx1 mbr.img
```It gives you an look at your MBR in hexadecimal. Note the famous 55 aa signature down in the right bottom corner, every sixteen bytes before that would represent one partition, and the top 446 bytes would be our bootloader's IPL.
Here's the codes for viewing it in decimal: ```
od -Ad -tu1 mbr.img
``` Now all we need to be able to do is become fluent in reading and writing in hexadecimal and decimal codes and we'll be all set! :-D (Herman).

---

### Post by Tyler Oderkirk on 2008-07-14
> **steve.horsley said:**
> 
```
sudo dd if=/boot/MBR-b4-win.image of=/dev/hda bs=446 count=1
```

After a Windows XP install stomped my GRUB, I used the Hardy LiveCD to mount my existing Linux partition and restore my saved MBR as Steve suggested above. Next, I rebooted into my existing Linux install and added the following entry for the new XP installation to **/boot/grub/menu.lst**:

```

title		Windows XP (is for weenies)
rootnoverify	(hd0,1)
chainloader	+1

```

Lastly, I ran **sudo grub-install /dev/sda** to write the new MBR which now allows me to choose XP or Linux at bootup.

-Tyler

---

