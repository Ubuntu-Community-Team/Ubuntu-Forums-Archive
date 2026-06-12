---
title: "SOS grub problem!!!!!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-06-12
Hi guys,
I have Kubuntu 7 installed on my machine.Well just today from aept i installed a few grub add-ons.They were mostly splash screens and other stuff. After i rebooted my system i am getting an error.
The error says...
[B][SIZE="2"]
Failed to read splashimage((hd0,8)/boot/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz

Press any key to continue....
[/SIZE][/B]

and after i press any key i ge the list of OS's on my system (Kubuntu (various options), Windows XP).

But if i select any of those OS's. i get the following error....

**[SIZE="2"]Error 18: Selected Cylinder exceeds maximum supported by BIOS[/SIZE]**

i'm stuck and unable to use my system........... please help asap

---

### Post by FleetAdmiral74 on 2007-06-12
It might help if you are a bit more particular about what you changed. Just thinking...

---

### Post by badguyanil on 2007-06-12
i installed grub splash images and all....

---

### Post by badguyanil on 2007-06-12
is there any  way i can change the existing grub/menu.lst file with the backup file. from live CD it doesn't let me saying i don't have permissions!!!!!!!!!

---

### Post by southernman on 2007-06-12
To get your system booting again, try reinstalling grub for starters.

Boot from a LiveCD (Ubuntu, Kubuntu, Knoppix...) and open a terminal window and do the following:

> sudo grub
Then...
> find /boot/grub/stage1
With the output of the above command do
> setup (hd0)
Make sure that the (hd0) part is what the last command told you. When this finishes just type
> quit
Now reboot. Easy Peasy! ;)

Rinse and repeat as needed.  :p

---

### Post by badguyanil on 2007-06-12
this is what i get from your mentioned method........

> grub> find /boot/grub/stage1
 (hd1,8)

grub> setup(hd1,8)

Error 27: Unrecognized command

grub> setup(hd1)

Error 27: Unrecognized command

grub> setup (hd1)  

Error 12: Invalid device requested

grub> setup (hd1,8)

Error 12: Invalid device requested


**the smiley is actually 8

help!!!!!!!!!!!!

---

### Post by badguyanil on 2007-06-12
guys waiting for reply!!!!!!!!

---

### Post by drowner on 2007-06-12
There is no space after setup in the first commands, beofre hd(1,8)

---

### Post by badguyanil on 2007-06-12
yeh tried both with and without space!!!!!!!!!!

---

### Post by drowner on 2007-06-12
> **badguyanil said:**
> yeh tried both with and without space!!!!!!!!!!


Oh I see.

---

### Post by southernman on 2007-06-12
> **drowner said:**
> There is no space after setup in the first commands, beofre hd(1,8)
!

---

### Post by southernman on 2007-06-12
Do it all over again, except this time do this before the setup command.

> root (hd1,8)

I learnt how to do this the really hard way, by searching google.

---

### Post by badguyanil on 2007-06-12
i see a file named menu.lst.070613071554 int he grub folder which i think is a backup of original menu.lst... anyways i can replace the one present now with this file?????? well thats what a backup is for!!!!

---

### Post by badguyanil on 2007-06-13
i tried the steps again..
the grub prompt found the stage1, stage 2 and said fixed. but after rebotting i am getting the same error!!!!

Error 18.....

please help! i have installed quiet a few things on the kubuntu machine... dont want to erase all and install again!

---

### Post by badguyanil on 2007-06-13
help anybody!!!!!!!! reinstalling the OS is tedious!

---

