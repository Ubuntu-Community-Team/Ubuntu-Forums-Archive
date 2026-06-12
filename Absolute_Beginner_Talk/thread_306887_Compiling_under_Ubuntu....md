---
title: "Compiling under Ubuntu..."
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by serosis on 2006-11-25
I just want to found out what i'm missing here...

I'm trying to compile operafs which is a command that can mount 3DO game cd's but i get a file not found, and i'm wondering where i can get it...

here is what i get in terminal
> serosis@serosis-desktop:~/Desktop/operafs-1.0b2$ make -C /usr/src/linux-headers-2.6.15-27 M=$PWD modules
make: Entering directory `/usr/src/linux-headers-2.6.15-27'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-27/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/serosis/Desktop/operafs-1.0b2/main.o
  CC [M]  /home/serosis/Desktop/operafs-1.0b2/super.o
  CC [M]  /home/serosis/Desktop/operafs-1.0b2/dir.o
  CC [M]  /home/serosis/Desktop/operafs-1.0b2/file.o
  CC [M]  /home/serosis/Desktop/operafs-1.0b2/inode.o
  CC [M]  /home/serosis/Desktop/operafs-1.0b2/address.o
  CC [M]  /home/serosis/Desktop/operafs-1.0b2/misc.o
  LD [M]  /home/serosis/Desktop/operafs-1.0b2/operafs.o
  Building modules, stage 2.
  MODPOST
/bin/sh: scripts/mod/modpost: No such file or directory
make[1]: *** [__modpost] Error 127
make: *** [modules] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.15-27'


thanks for any help

---

### Post by junglepeanut on 2006-11-25
I am going to guess that you have all of build-essential since make works.

And that the readme tells you to do all the extra commands. If you are doing those yourself then you probably know way more than I do and I am wasting time. But if that is the case you may want to try in the programming forums.)

Also do you have all of the dependecies, it looks like it looked for something and could not find it.

I have no idea with this line but if you are using edgy, is the makefile using bash, as you might have to do a quick switch like with a driver install

sudo ln -sf bash /bin/sh
then after wards
sudo ln -sf dash /bin/sh

Just guessing. Hope this helps.

---

### Post by jerrykenny on 2006-11-25
WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-27/Module.symvers
 is missing; modules will have no dependencies and modversions.

Are you sure you've got kernel-headers installed?

---

### Post by serosis on 2006-11-25
i'm pretty sure i got them installed

---

