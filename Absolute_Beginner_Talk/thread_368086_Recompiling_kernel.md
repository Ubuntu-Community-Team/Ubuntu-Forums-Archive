---
title: "Recompiling kernel"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by t111 on 2007-02-22
I'm trying to compile wireless adapter drivers and having failures
and I was advised to disable SMP in the kernel.  Does anyone 
know where I can find a good set of documents showing
how to do this for a beginner?

---

### Post by Bachstelze on 2007-02-22
I highly doubt you need to do that. What is the adapter you're trying to install ?

---

### Post by t111 on 2007-02-22
> **HymnToLife said:**
> I highly doubt you need to do that. What is the adapter you're trying to install ?

I'm trying to install the rt2570 drivers for a USB wireless adapter.
Whenever I try to compile them I get a message "error: sorry, this 
nice piece of code was not designed with SMP in mind" and 
"rt2570.ko failed to build make: *** [module] Error 1" 

 I'm running edgy eft, My linux headers are 2.6.17-11- generic

I went to the website where I obtained the rt2570 drivers and
was advised to disable SMP in the kernel.

---

### Post by Bachstelze on 2007-02-22
The easy way would be to grab the non-SMP 386 kernel with

```
sudo apt-get install linux-image-386
```

If you decide to follow my signature and recompile your kernel, here's what you need to do :

1) get the source code and other suff needed to compile : sudo apt-get install linux-source build-essential
2) cd /usr/src
3) extract the source code : sudo tar xjvf linux-source-2.6.17.tar.bz2		
4) Make a symlink to /usr/src/linux : sudo ln -s linux-source-2.6.17 linux
5) cd linux
6) Configure your kernel to disable SMP : gksudo make xconfig
7) Once you're done, save the config and exit
8) It's time to build the kernel image : sudo make bzImage
9) We build the kernel modules now : sudo make modules
10) And we install them : sudo make modules_install
11) We install the kernel image in /boot : sudo make install

You might need to modify your GRUB config to boot the newly installed kernel, don't hesitate to ask if you don't know how to do it.

---

### Post by t111 on 2007-02-22
> **HymnToLife said:**
> The easy way would be to grab the non-SMP 386 kernel with

```
sudo apt-get install linux-image-386
```

If you decide to follow my signature and recompile your kernel, here's what you need to do :

1) get the source code and other suff needed to compile : sudo apt-get install linux-source build-essential
2) cd /usr/src
3) extract the source code : sudo tar xjvf linux-source-2.6.17.tar.bz2		
4) Make a symlink to /usr/src/linux : sudo ln -s linux-source-2.6.17 linux
5) cd linux
6) Configure your kernel to disable SMP : gksudo make xconfig
7) Once you're done, save the config and exit
8) It's time to build the kernel image : sudo make bzImage
9) We build the kernel modules now : sudo make modules
10) And we install them : sudo make modules_install

11) We install the kernel image in /boot : sudo make install

You might need to modify your GRUB config to boot the newly installed kernel, don't hesitate to ask if you don't know how to do it.


Thanks for the help,  I think I'll just get the linux-image-386, so what
entries would I hve to edit into the grub config?  I've already edited the
grub setup to put in a dual boot setup into menu.lst, is this also the file
to modify for the new kernel?

---

### Post by Bachstelze on 2007-02-22
If you install a linux-image, it should update your GRUB config automagically. Then reboot your machine and choose the 386 kernel in the menu.

---

### Post by t111 on 2007-02-22
> **HymnToLife said:**
> If you install a linux-image, it should update your GRUB config automagically. Then reboot your machine and choose the 386 kernel in the menu.

Thanks, I appreciate your help

---

