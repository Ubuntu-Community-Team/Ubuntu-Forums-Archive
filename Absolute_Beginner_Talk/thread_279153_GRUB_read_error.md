---
title: "GRUB read error"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by crash6914 on 2006-10-17
Ok, i installed ubuntu, and then decided that i prefered kubuntu. So i installed kubuntu, and chose to erase my entire hard disk. The installation went fine, and it said it was completed successfully. But when i try to boot into my new OS, it just comes up with 'GRUB read error'. I know vaguely what GRUB is, but it's hardly being specific. Can anyone help me out?

---

### Post by bulldog on 2006-10-17
You can reinstall GRUB with the live cd.
Or you can mount your install with the live cd to see what's wrong with GRUB.

To install GRUB do the following,

```
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 


[code]sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.
[/code]

---

### Post by crash6914 on 2006-10-17
Cheers, i'll try it later today.

---

### Post by crash6914 on 2006-10-18
I did exactly what you said and it made no difference what so ever. Anymore suggestions?

---

### Post by bulldog on 2006-10-18
Can you put your menu.lst here?
```
gedit /boot/grub/menu.lst
```

And the outcome of```
sudo fdisk -l
``` l as in like.

---

### Post by crash6914 on 2006-10-19
Ok i may well be doing something wrong but it seems to me that the folder /grub doesn't exist. Also, i don't understand what my problem is as i've tried re-installing kubuntu several times with the option to erase my HD, so why am i getting the same error over and over again. I am not dual booting, so would it make any difference if i were to plug my HD into another rig and format it manually before reinstalling?

---

