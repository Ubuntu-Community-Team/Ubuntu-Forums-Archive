---
title: "bootup problem"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-04-14
Ubuntu suddenly stopped booting up, i get the usplash screen and after that it stays and a green line appears at the bottom of the screen, i tried removing and re-installing xserver-xorg, xorg-driver-fglrx and xserver-xgl since i have beryl but all that dind't work 
when i do ```
sudo aticonfig --overlay-type=Xv
```
i get a message saying
```
aticonfig: error while loading shared libraries: libXrender.so.1: cannot open shared file: No such file or durectory
```

any help?
because i don't feel like removing Ubuntu and re-installing it!!!
Thanks

---

### Post by xopher on 2007-04-14
> i get the usplash screen and after that it stays and a green line appears at the bottom of the screen

If the usplash screen stays, then how could you remove things etc? This means your system hasn't even booted yet. (Usplash is the screen you get directly after GRUB).

Still the error you are getting implies you don't have libXrender.so.1 installed, so I'd try installing that.

The closest packages I could find are: ibxrender-dev, libxrender1, libxrender1-dbg

---

### Post by RaZer0r on 2007-04-14
there are problems with the current kernel update, try booting from the previous kernel installed in your grub...
When booted up do not login
press alt + ctrl + F1 to get to the text based console
login with your username and pass
Do:
```

sudo apt-get update &&  sudo apt-get dist-upgrade
sudo reboot

```
and see if that worked, if not, just stay booting from the previous kernel for a moment, there will be updates released soon

---

### Post by xopher on 2007-04-14
The current one should work just fine.

> linux-image-2.6.20-15-generic              2.6.20-15.**25** 

---

### Post by Mazen on 2007-04-14
i remember doing an update, and usualy when i do so i don't look at the programs to be updated, and after that it needed a reset, so i did and the grub menu changed, it was displayihg 2 kernels, i edited the grub menu by pasting an old menu.lst i had!(just the OS part since i have Windows XP and i wrote them all in sequence in the old one)
and after that it didn't boot no more! i think that should be the problem!
i just checked the grub menu and it refers to the right place, my kernel is 2.6.17.10-generic

---

### Post by Mazen on 2007-04-14
> **xopher said:**
> If the usplash screen stays, then how could you remove things etc? This means your system hasn't even booted yet. (Usplash is the screen you get directly after GRUB).

Still the error you are getting implies you don't have libXrender.so.1 installed, so I'd try installing that.

The closest packages I could find are: ibxrender-dev, libxrender1, libxrender1-dbg

Man i do all that when i boot in recovery mode!

---

