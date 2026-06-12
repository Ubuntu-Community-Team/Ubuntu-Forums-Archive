---
title: "install ubuntu on a ibook g3 700"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by unseenbeing on 2007-07-24
i just bought this laptop used
the guy who owned it put xubuntu on it and i want to change it to ubuntu
i have the 6.10 live cd but it wont boot to it. instead it just loads xubuntu.
is there a way that i can just change to ubunutu through terminal?

---

### Post by punx45 on 2007-07-24
you can install it with
```
sudo apt-get install ubuntu-desktop
```

then reboot and select ubunu at the login screen.

but i would guess that xubuntu is installed because ubuntu ran too slow on that system.

---

### Post by unseenbeing on 2007-07-24
this laptop should run it pretty good
700mhz amd with 256 mb ram
my old laptop has a 600mhz with 256 mb ram and runs it just fine

---

### Post by unseenbeing on 2007-07-24
k just finished and its still loading xubuntu
how can i get rid of xubuntu

---

### Post by bigfox on 2007-07-24
If you hold the C key down on Mac's when you turn them on, it forces them to boot from CD.

Also, you need to have the PowerPC version of Ubuntu for it to work on a G3.  The intel versions will not work on PowerPC macs.

---

### Post by unseenbeing on 2007-07-24
ah thank you for clearing that up

where can i find the powerpc version of ubuntu

---

### Post by whorton on 2007-07-24
The only version I found for a G3 Processor was the 6.06 version of Ubuntu (Dapper Drake).
Below is the path for the Download:

[http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/)

---

### Post by testube_babies on 2007-07-24
You can get 7.04 here, but I'd recommend sticking to 6.06 for the specs of that laptop:
[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

EDIT: 6.10 is here:
[http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)

---

### Post by punx45 on 2007-07-25
the laptop already has xubuntu.   the only difference is the desktop environment.  he doesn't need to reinstall.   if anything there is more of an opportunity for something to go wrong.

if you installed the ubuntu desktop package, when you are at the login screen there should be an option in the bottom left corner to use a different environment.   that is where you can choose ubuntu rather than xubuntu.   at that time you can also set it to be the default.   you will then also be able to still go back to xubuntu if you choose to.

i had ubuntu running on a 1Gh PIII with 512 ram and it was still a little sluggish.

if you decide you dont want to keep xubuntu you should be able to remove it with apt. (pretty sure)   try 
```
sudo apt-get remove xubuntu-desktop
```   
you can man apt-get to double check that.

---

### Post by unseenbeing on 2007-07-25
i did a fresh install of ubuntu 7.04
its runs very smooth

---

