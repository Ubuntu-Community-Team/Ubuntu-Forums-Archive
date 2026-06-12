---
title: "i'm new to ubuntu"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by connel on 2006-12-21
I have just switched from openSUSE 10.2 so I'm not sure whether i should count as as an absolute beginner, so feel free to move this post if necessary 

1) I am used to using su so what exactly is sudo and how do i use it.

2) Also is there a good how to on installing nvidia graphic cards. I have tried installing NVidia binary X.Org driver using the add/remove applications program and running

sudo nvidia-glx-config enable

like the package description tells me but i get the following:

Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

3) Also i have two FAT partitions. How could i mount them so that i could go to (for example) /windows to access my windows partition (i dual boot) because on openSUSE i could mount all my partitions when i installed it.

4) Also how can i theme Grub because at the mo it is just a black screen with white writing. (on openSUSE it was a nice blue screen)

5) Also whats the best way to use Beryl nVidia drivers or AIGLX.

I know it probably sounds like i am saying openSUSE is better than Ubuntu. That not what what I am sayings its just I'm not used to using Ubuntu thats all.

---

### Post by Bachstelze on 2006-12-21
1) [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

2) [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

3) [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

don't know about 4) and 5), sorry :p

---

### Post by 23meg on 2006-12-21
> 1) I am used to using su so what exactly is sudo and how do i use it.[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> 2) Also is there a good how to on installing nvidia graphic cards. 
[http://www.ubuntuforums.org/showthread.php?t=281823](http://www.ubuntuforums.org/showthread.php?t=281823)
> 
3) Also i have two FAT partitions. How could i mount them so that i could go to (for example) /windows to access my windows partition (i dual boot) because on openSUSE i could mount all my partitions when i installed it.They should be automatically mounted. Don't you see icons for them on your desktop, or on your "Places" menu?
> 
5) Also whats the best way to use Beryl nVidia drivers or AIGLX.nVidia drivers will be faster but there's a known "black window bug" that affects many cards. If you get that, you can start Beryl with "--use-cow --force-aiglx" to use AIGLX.

---

### Post by scar_freewill on 2006-12-21
I hope this can help you:

Note if you want to use beryl you'll need beta nv drivers so "NO2" woudn't be of any use :P

NO2) [https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper) (I'm on edgy and I used "METHOD 1" it works the for me the fastest, esaiest and best...

NO5) This is how I used beryl:
[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA) (Method One)

CYA! :mrgreen:

---

### Post by connel on 2006-12-21
Thanks for the fast replies! I now understand sudo, I have successfully installed the nVidia drivers and i now have beryl working! However i have two FAT partitions I can't access. (I can boot to windows XP through grub and access both my FAT partitions). Also i still would like to have a nice Ubuntu theme for my grub. Could anybody help me with these please!?

(BTW can i say how impressed i am with Ubuntu. It is much, much faster (especially at booting and shutting down) than SUSE and the package manger actually works! I also love the Human theme. However installing the nVidia drivers were more difficult to do on Ubuntu than SUSE.)

EDIT: Also i have just noticed that the updater is not starting on startup? thank for all your help

---

### Post by connel on 2006-12-22
i have successfully mounted my fat partitions on Ubuntu using this guide:
[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/).
Now the only problem i have left is that grub is ugly. Is there a gui tool that i can use to skin it my self or can u download themes for grub somewhere?

---

### Post by raul_ on 2006-12-22
Grub themes? Lol that's a new one :) never really thought of that..i'll see if i find something

EDIT: who would say:

[http://www.schultz-net.dk/grub.html]("http://www.schultz-net.dk/grub.html")

---

### Post by connel on 2006-12-22
It's just I'm used to openSUSE and that has a lovely blue background and different coloured text and font?

EDIT: this is what I meant:
[http://www.ubuntuforums.org/showthread.php?t=208855](http://www.ubuntuforums.org/showthread.php?t=208855)

---

### Post by raul_ on 2006-12-22
i think this one is cool
[http://www.gnome-look.org/content/show.php?content=29962]("http://www.gnome-look.org/content/show.php?content=29962")

---

### Post by BarfBag on 2006-12-22
I'm one of the few that prefers a black Grub screen.  I must admit, though.  The SUSE ones have always been pretty sexy.

---

