---
title: "fstab conf"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by blueoyster on 2007-02-13
i aded this line to my fstab file to allow me to mount a partition on a new hard drive:

**/dev/sda6       /media/new      ext3    noauto,user,exec,rw,async 1 1** 

but I get an error:
[B]
[mntent]: warning: no final newline at the end of /etc/fstab[/B]

when i try to** sudo mount -a**

i dont know what to do. any help is appreciated

---

### Post by highneko on 2007-02-13
> **blueoyster said:**
> i aded this line to my fstab file to allow me to mount a partition on a new hard drive:

**/dev/sda6       /media/new      ext3    noauto,user,exec,rw,async 1 1** 

but I get an error:
[B]
[mntent]: warning: no final newline at the end of /etc/fstab[/B]

when i try to** sudo mount -a**

i dont know what to do. any help is appreciated
The error in my opinion suggests there's a newline at the bottom of your fstab file and isn't allowed. Or maybe there has to be a newline. In any case it was probably caused by someoene editing the fstab file. You could compare it to a backup fstab file if you have one; Maybe using the command diff. Good luck, have fun.

---

### Post by orb9220 on 2007-02-13
> no final newline at the end of /etc/fstab

did you hit enter key after entering the line?

Don't know if that is the problem but newline is the end of a line as the enter or return key.

---

