---
title: "[SOLVED] root@pcname-desktop:~#_"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by burnetbj on 2008-02-01
Hi all

I recently moved my SATA hdd from one machine to another do to cooling and what not. Both PC's have AMD dual core, Asus A8N32 motherboards, eVGA 7800gt .....same PCs really 

After the migration I can no longer boot. The WinXP partion still works fine and the LiveCD gets me to the ext3 partitions and all my data works fine just cant boot 

During normal boot i get Loading this loading that please wait .....everything loads OK seems like its gonna do it but then at the end i get this promt

pcname@pcname-desktop:~$_ 

During recovery mode i get 

root@pcname-desktop:~#_ 

what is this waiting for me to do here .....apparently i need to give her a command of some kind here

/dev/sda1 = WinXP 120 Gb
/dev/sda2 = Ubuntu 28Gb
/dev/sda4 = storage 328 Gb 
/dev/sda3 = swap 3 Gb

Any help would greatly be appreciated .....reloading shouldnt be too hard but I would like to learn how to over come this as it should be reasonably easy as I shut down OK and reinstalled OK and the HDD is fine and WinXP is even fine crazy enough Ubuntu is mad at me

---

### Post by Dr Small on 2008-02-01
Could be due Xorg not recognizing graphics card.
Try reconfiguring Xorg:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by burnetbj on 2008-02-01
OK just tried and came up with display resolustion options ....so i picked correct one and then 

gave me a warning that this could cause issues and took me back to promt this is acking me for something ....do i reboot is there a command to restart from here? 

root@pcname-desktop:~#_

I thought Gutsy had fail safe 

Thanks for the help

---

### Post by icechen1 on 2008-02-01
Try sudo startx , maybe x server isn't started.

---

### Post by Nythain on 2008-02-01
you could try typing
```

startx

```or quite possibly
```

sudo /etc/init.d/gdm restart

```and seeing if it will load xorg from command line...
if not, could you post any errors it spits out at you???
also, possibly get the output of
```

cat /etc/X11/xorg.conf

```so we can see what your xorg.conf looks like... basically, for some reason or another, the only thing i can guess is a random hardware change is keeping X from loading, so its tossing you to a command prompt

and as for rebooting from command prompt you have a few options
```

sudo shutdown -r now

```
or
```

sudo reboot

```
or to just power off
```

sudo shutdown now

```
and i cant remember if the other alternative is
sudo poweroff or sudo powerdown

---

### Post by burnetbj on 2008-02-01
Thanks to all for helping I reconfigured X and then I didnt know what to do so I tried ctrl +alt+delete

this restarted it suprisingly and WHAMM!! 


Dang this just wanted me to go to a lower resolution :) thanks again ...have no idea how it got so high I never changed it but oh well its fixed thanks to this great community 

Thanks again ......can someone change this to a resolved issue ?

---

### Post by Dr Small on 2008-02-01
> **burnetbj said:**
> Thanks to all for helping I reconfigured X and then I didnt know what to do so I tried ctrl +alt+delete

this restarted it suprisingly and WHAMM!! 


Dang this just wanted me to go to a lower resolution :) thanks again ...have no idea how it got so high I never changed it but oh well its fixed thanks to this great community 

Thanks again ......can someone change this to a resolved issue ?
You can do that :D
Thread Tools > Mark as Solved

---

### Post by burnetbj on 2008-02-01
OK thanks again

---

