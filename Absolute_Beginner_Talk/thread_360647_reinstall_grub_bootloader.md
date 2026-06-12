---
title: "reinstall grub bootloader?"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by AGSzabo on 2007-02-13
hello all,

just let me know if i am right. i installed ubuntu 6.10 and after that i installed windos. windos killed grub away from the mbr. to get grub back into the mbr i am going to:

- boot from the cd
- open a shell
- sudo su
- mount /dev/hda4 /mnt
- mount /dev/hda5 /mnt/boot
- grub-install --root-directory=/mnt /dev/hda

is this correct? does it work this way?

---

### Post by bodhi.zazen on 2007-02-13
I am not 100 % sure with a separate boot partition, but I think you can re-install grub as follows:

Boot the live CD, open a terminal.

```
sudo grub
```

At the grub prompt:

```
root (hd0,4)
setup (hd0)
quit
```

Reboot, should be good to go ;)

---

### Post by AGSzabo on 2007-02-13
thank you. what do you mean you THINK. does it work or not?

---

### Post by bodhi.zazen on 2007-02-13
Well, those commands will re-install grub to the MBR.

The part I am not sure about is if the first grub command is 

root (hd0,4) or root (hd0,3)

hd0,4 = your boot partition in grub speak :)

---

### Post by AGSzabo on 2007-02-13
yes, grubs (hd0,4) is my /dev/hda5 my boot partition

---

### Post by bodhi.zazen on 2007-02-13
go ahead, give it a try ...

---

