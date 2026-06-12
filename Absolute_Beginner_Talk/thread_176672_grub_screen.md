---
title: "grub screen"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by shurguywutt on 2006-05-15
My grub screen has about 15 different versions of ubuntu on it, but I only use about 2 or 3.  How do I get rid of the ones I dont want?

---

### Post by tkjacobsen on 2006-05-15
Eighter you could uninstall non used kernels and then update grub:```
sudo update-grub
```

Or you could outmark non used entries in /boot/grub/menu.lst with # - This is preferable if you don't know witch kernels to remove

---

### Post by Sutekh on 2006-05-15
You could use the command```
sudo update-grub
```But I have a feeling that it only affects entries that are contained by the 
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

``` and
```
### END DEBIAN AUTOMAGIC KERNELS LIST

``` I could be wrong of course.

You can always edit it the list with
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```and comment the entries you don't want with a # sign

---

### Post by ajgreeny on 2006-05-15
Assuming you mean different kernels and not totally separate installations, you can just edit your /boot/grub/menu.lst by entering 
"sudo gedit /boot/grub/menu.lst"
and deleting (or preferably commenting out [with # at the start of the line] the entries for the kernels you don't want to show).

Alternatively you can uninstall the kernels which you don't need in synaptic, but make sure you are totally happy with the kernel you always boot to first as it can occasionally be useful to have a fall-back position of an older tried and trusted kernel available.  Look for the kernel numbers in the boot menu, make a note of them and then uninstall using synaptic.

---

