---
title: "amending grub"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by cbradley on 2008-01-05
hi everybody

I want to add a further entry (another boot partition) on my grub screen - how do I do it?.

I tried the CLI and got hopelessly lost, I've got a cd called supergrub which I tried could not make it do what I wanted

---

### Post by eggdeng on 2008-01-05
It depends on how your partitions are set up. Post the output of 
```
sudo fdisk -l
```
and tell us how you did the install. Did you install Ubuntu over XP, and then Fedora? Did you install Grub to the MBR both times? Post the output of ```
cat /boot/grub/menu.lst
``` for good measure.

---

### Post by mikewhatever on 2008-01-05
First, backup the existing menu.lst file. <sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup>

Now, open the file for editing, press alt+f2, type <gksudo gedit /boot/grub/menu.lst>

You should now be able to modify the file. If you do not know what to add, tell us more about what you are trying to do. What OS, on which partition are you trying to add?

---

### Post by cbradley on 2008-01-05
hi

I don't know how to post the output from the terminal but here is a rundown
?dev/sda1 WinXP
/dev/sda2 Ubuntu
/dev/sda3 Fedora

Winxp first  Ubuntu second & fedora last but I told it not to overwrite the grub on /dev/sda1 because then I wouldn't have had Ubuntu think it would be simple to change the grub parameters
..

---

### Post by eggdeng on 2008-01-05
Back-up first as Mike suggests. Then copy and paste in a terminal. 
```
sudo gedit /boot/grub/menu.lst
```

In the file that opens, below the entry for XP add the lines

```
#Added by cbradley
title           Fedora Linux
root            (hd0,2)
chainloader      +1
```

Save and reboot.

---

### Post by cbradley on 2008-01-05
hi
I don't know the kernel version of the fedora core 7 and initrd parameter sure it documentary to grub

---

### Post by eggdeng on 2008-01-05
I assumed you had installed Fedora's Grub to the first sector of sda3, in which case you wouldn't need any more data.

---

### Post by cbradley on 2008-01-05
hi 
I got a error 13 invailid executale.
So that is grub  sortred  but i need to reistalll fedora again

---

