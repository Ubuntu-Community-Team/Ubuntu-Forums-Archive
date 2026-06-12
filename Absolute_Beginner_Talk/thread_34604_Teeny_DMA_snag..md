---
title: "Teeny DMA snag."
date: 2005-05-15
forum: Absolute Beginner Talk
---

### Post by davidgypsy on 2005-05-15
.

---

### Post by monchichi on 2005-05-15
There's a program called hdparm which enables you to do this sort of thing.

Run the following:

```
sudo hdparm -d1 /dev/hdc
``` (Replacing hdc with hdd or whatever your drive is) You can use hdparm to fine tune the performance all of your ide drives, but be careful!

---

### Post by jeremy on 2005-05-16
If that doesn't work, then read this post; [http://ubuntuforums.org/showpost.php?p=93238&postcount=5](http://ubuntuforums.org/showpost.php?p=93238&postcount=5)

---

### Post by Stormy Eyes on 2005-05-16
[QUOTE=davidgypsy]Ok, so I hit a teeny snag... I can't work out how to enable DMA on my CD rom drive. Can anyone tell me how to do this?

Thanks![/QUOTE]

Monchichi has the right idea, but I'd suggest **sudo hdparm -k1 -c3 -d1 /dev/hdc** instead, in order to enable DMA, 32-bit I/O, and make the drive keep these settings. And do it to your other CD-ROM and hard drives too.

---

### Post by davidgypsy on 2005-05-20
Thanks a whole bunch guys!! I knew there must be some simple way to do this. :)
I am just learning how to do all this stuff, and it is a great help to have a forum like this!

---

### Post by davidgypsy on 2005-05-21
[QUOTE=Stormy Eyes]Monchichi has the right idea, but I'd suggest **sudo hdparm -k1 -c3 -d1 /dev/hdc** instead, in order to enable DMA, 32-bit I/O, and make the drive keep these settings. And do it to your other CD-ROM and hard drives too.[/QUOTE]


OK! So that did not work and my DVD's still jump when I try to play them. Any ideas?

---

### Post by Bob D. on 2005-05-21
Are you positive DMA is active? Run the following and post the results:

 ```
sudo hdparm /dev/hd*
``` 

replacing '*' with your DVD drive letter.

Bob

---

### Post by davidgypsy on 2005-05-21
[QUOTE=davidgypsy]OK! So that did not work and my DVD's still jump when I try to play them. Any ideas?[/QUOTE]

I just checked the unofficial Ubuntu Guide, and it showed how to enable DMA to speed up a drive, and it worked. This guy (Chua Wen Kiat) should get an award or something! Thanks, your guide is GREAT STUFF! :)  :)  :)  :)  :)

---

