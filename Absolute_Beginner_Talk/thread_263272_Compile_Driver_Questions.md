---
title: "Compile Driver Questions"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by lgpatterson on 2006-09-22
I am extremely new to Linux and chose ubuntu as my first linux os. Please be patient with me. I am trying to compile the source driver for an onboard network card on a laptop. When I do the ./Makefile I get this message:

./Makefile: line 1: obj-m: command not found
./Makefile: line 3: shell: command not found
./Makefile: line 3: KERNELDIR: command not found
./Makefile: line 4: shell: command not found
./Makefile: line 4: PWD: command not found
./Makefile: line 5: shell: command not found
./Makefile: line 5: MODULE_INSTALLDIR: command not found
./Makefile: line 7: all:: command not found
./Makefile: line 8: MAKE: command not found
./Makefile: line 8: KERNELDIR: command not found
./Makefile: line 8: PWD: command not found
./Makefile: line 8: -C: command not found
./Makefile: line 10: clean:: command not found
./Makefile: line 13: install:: command not found
./Makefile: line 14: MODULE_INSTALLDIR: command not found
mkdir: missing operand
Try `mkdir --help' for more information.
./Makefile: line 15: MODULE_INSTALLDIR: command not found
./Makefile: line 16: MODULE_INSTALLDIR: command not found
./Makefile: line 17: MODULE_INSTALLDIR: command not found
./Makefile: line 18: MODULE_INSTALLDIR: command not found
install: target `tifm_sd.ko' is not a directory
FATAL: Could not open /lib/modules/2.6.15-27-386/modules.dep.temp for writing: Permission denied

I tried using sudo nautilus but no luck. All replies are greatly appreciated for this very green user.

Thanks

---

### Post by xXx 0wn3d xXx on 2006-09-22
> **lgpatterson said:**
> I am extremely new to Linux and chose ubuntu as my first linux os. Please be patient with me. I am trying to compile the source driver for an onboard network card on a laptop. When I do the ./Makefile I get this message:

./Makefile: line 1: obj-m: command not found
./Makefile: line 3: shell: command not found
./Makefile: line 3: KERNELDIR: command not found
./Makefile: line 4: shell: command not found
./Makefile: line 4: PWD: command not found
./Makefile: line 5: shell: command not found
./Makefile: line 5: MODULE_INSTALLDIR: command not found
./Makefile: line 7: all:: command not found
./Makefile: line 8: MAKE: command not found
./Makefile: line 8: KERNELDIR: command not found
./Makefile: line 8: PWD: command not found
./Makefile: line 8: -C: command not found
./Makefile: line 10: clean:: command not found
./Makefile: line 13: install:: command not found
./Makefile: line 14: MODULE_INSTALLDIR: command not found
mkdir: missing operand
Try `mkdir --help' for more information.
./Makefile: line 15: MODULE_INSTALLDIR: command not found
./Makefile: line 16: MODULE_INSTALLDIR: command not found
./Makefile: line 17: MODULE_INSTALLDIR: command not found
./Makefile: line 18: MODULE_INSTALLDIR: command not found
install: target `tifm_sd.ko' is not a directory
FATAL: Could not open /lib/modules/2.6.15-27-386/modules.dep.temp for writing: Permission denied

I tried using sudo nautilus but no luck. All replies are greatly appreciated for this very green user.

Thanks

sudo apt-get update
sudo apt-get install build-essential

---

### Post by podunk on 2006-09-22
I found this page very helpful:
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by lgpatterson on 2006-09-23
Thanks for the replies. I tried sudo apt-get update and build essential. It said that the newest was already installed. I tried the ./Makefile again just to see if those commands did do something but I got the same error.

I am searching the page posted by podunk to see if I can find anything there. 

Thanks to yo both for helping. I appreciate it.

---

