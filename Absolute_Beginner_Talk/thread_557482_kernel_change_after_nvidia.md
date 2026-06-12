---
title: "kernel change after nvidia"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by phatdad on 2007-09-22
I had evrything working okon generic kernal. Then i installed the nvidia driver for my card, geforce fx5200, and on reboot the x server needed to be reconfigured, which I've managed. However my USB modem has stopped working now. Do I need to reinstall the modem? Should the kernal have changed like that and do I need to recompile everything? 
Please help

---

### Post by BrumleyGap on 2007-09-22
Sorry, I didn't catch how your kernel changed. Did you update to a new release or are you saying that your nvidia driver did something to it?

---

### Post by phatdad on 2007-09-22
I think it must have been the Nvidia driver. I am on a windows machine posting this as I can't get the modem to work under Ubuntu. It was working with the generic kernel. 

I now have the extra -386 kernel showing in Grub. Booting into this needed the x server to be reconfigured. It won't run if I try to boot into the generic kernel

---

### Post by ajgreeny on 2007-09-22
Sounds as if you have a new kernel, and I believe you need to reinstall the nvidia drivers each time there is a kernel upgrade.  Try doing that for the new kernel and see if it helps.

---

### Post by phatdad on 2007-09-22
Thanks for the replys. Been back in Ubuntu and tried to get the modem working using eagle-atm. I got as far as 'make' and got an error.

dad@ubuntu:~/ueagle-atm-1.3$ make
make -C /lib/modules/2.6.17-10-386/build M=/home/dad/ueagle-atm-1.3
make[1]: Entering directory `/lib/modules/2.6.17-10-386/build'
make[1]: *** No targets specified and no makefile found. Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-386/build'
make: *** [all] Error 2

I haven't tried to mess with the Nvidia bit yet, but I think somethings wrong as there is no Nvidia splash screen.

Can anyone help? I have downloaded the -386 headers on this windows machine and then installed the package on the ubuntu box. So I think that's all in order. Is it anything to do with gcc?

---

