---
title: "make command"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by blull on 2005-12-30
I'm fairly new to linux, but I do know that I need to be able to use the make and make install commands in order to compile and install programs/drivers.  For some reason, signed on in the root console, or just in the console period, it is not recognizing either of these commands.  It just says make: command not found and its impossible to run a makefile.  Is there something special about ubuntu or another way I need to compile?  

PS im trying to install a usb wireless network card driver for my wg111 network card, if anyone has any experience with this.

---

### Post by jpkotta on 2005-12-30
You need a toolchain.  ```
sudo apt-get install build-essential
```
For a driver, you need the linux headers ```
sudo apt-get install linux-headers-[version]
```  You can find the version with ```
uname -a
```

Try [this]("https://wiki.ubuntu.com/ConfigureMakeMakeInstall?highlight=%28make%29") too, though drivers usually don't have a ./configure step.

I'm sure I'm forgetting something, though.

---

