---
title: "Reinstall Ubuntu? (nvidia driver problem)"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Hymie on 2007-05-14
Is it possible to comletely reinstall Ubuntu? I messed up my laptop, and think it's best to start from scratch. 

I have a Toshiba Satelline. I activated my Nvidia graphics card. When I enter the login screen upon restarting, my screen turns black then gray. I have to do a hard reset.

I searcehd forums and tried following the advice on how to reconfigure my xserver. I had no luck, so I surrender.

Thanks,
hymie

---

### Post by Martje_001 on 2007-05-14
Of course. Pop in the Ubuntu disk and follow the instructions. Make a backup of your data!

---

### Post by Hymie on 2007-05-14
Thanks for your response.

I tried that but ubuntu just loads from the hard drive, even when I select boot from CD. Maybe I just did not burn the CD correctly? I will check this evening.

Thanks

---

### Post by kinematic on 2007-05-14
you could just repair your ubuntu install and learn something in the proces.
first i would boot into recovery mode(that boots you to a command line as root)and edit your
xorg.conf with nano.
```
nano -w /etc/X11/xorg.conf
```
locate the section "device" and change the driver form nvidia to nv.
then close with Ctrl>x and answer yes if asked to save the changes.
now you can log out as root,log in as user and
```
startx
```
to start the graphical desktop.
now you can search for answers why it went wrong the first time :) 
if you still want to reinstall check the bios to see if the cd drive is the first boot device.

---

### Post by Hymie on 2007-05-14
Thanks,
I have logged in at root, and am at the xorg.conf, but I cannot locate device.

---

### Post by Miroku on 2007-05-14
since i hate having to do hard resets, i do ALT + SysRq + b

sysrq = print screen key

i dont kno if this has any adverse effects but i find it easier just doin this.

and keep tryin with the nvidia card, it took me like a week to figure mine out but eventually it was all good.

this was an awesome guide:

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

thats for feisty, i dont know what you are using so here is the edgy:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

good luck!

---

### Post by Hymie on 2007-05-14
wow, I actually tried a different method via
sudo dpkg-reconfigure xserver-xorg

I loaded the generic driver 'vesa'
typed xstart

and bingo I can see my screen again, now all I have to do is get the nvidia card installed.


Thanks for all.

---

