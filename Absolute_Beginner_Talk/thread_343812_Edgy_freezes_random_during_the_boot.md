---
title: "Edgy freezes random during the boot"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by mobal on 2007-01-22
hi'

i have a big problem. random boot ubuntu freezes. (sometimes it boots but somtimes the loading bar stops and i wait 10 sec 5 minits nothing...) so how can i solve this problem?

thanks'

mobal from hungary.

---

### Post by guysmiley25 on 2007-01-22
This isnt really a solution but try disabling usplash. Thats what display that loading thing while the computer boots.

You can either remove it or disabling it.

To Remove:
```
sudo apt-get remove usplash
```

To Disable
```
sudo nano /boot/grub/menu.lst
```

And change where it says something like this:
```
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
```

to:
```
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet
```

Now if at least thats not causing the problem, it should help detect what is.

---

### Post by mobal on 2007-01-22
thanks! i will try it! if next the boot fails i will post it.

another questions /etc/modules not load speedstep-centrino at boot. what to do?

---

### Post by mobal on 2007-01-22
news: checking file system... fsck [ok]

and in this point the boot stops. :confused:

---

### Post by guysmiley25 on 2007-01-22
Not too sure about modules. Maybe not adding to the list is eniough.

[This]("http://ubuntuforums.org/showthread.php?t=338267") guy seems to be having similar problems.

Have you tryed [this]("http://www.ubuntuforums.org/showthread.php?t=248867") How to?

---

### Post by guysmiley25 on 2007-01-22
I just did a reboot then to see what happens on my machine at that point and for me thats when gdm starts up.

I think there is some sort of log you can access. You could try something like that maybe? Sorry I can't help you much more than that.

---

### Post by mobal on 2007-01-22
> **guysmiley25 said:**
> Not too sure about modules. Maybe not adding to the list is eniough.

[This]("http://ubuntuforums.org/showthread.php?t=338267") guy seems to be having similar problems.

Have you tryed [this]("http://www.ubuntuforums.org/showthread.php?t=248867") How to?

this guy is me :D

Yes i did this howto and works fine but at boot i can't load this module only. :(

---

### Post by guysmiley25 on 2007-01-23
Lol should of checked that! Sorry I can not help but it my guess is that it has something to do with "speedstep-centrino". Hopefully you will solve this problem or someone who can will come along.

---

