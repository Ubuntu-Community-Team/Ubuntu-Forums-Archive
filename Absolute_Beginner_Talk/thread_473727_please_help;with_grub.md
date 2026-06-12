---
title: "please help;with grub"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by timo_01 on 2007-06-14
i think i messed or overwrote my grub because i get only ```
grub > 
```as the startup. with also minimal BASH like line editing is supported...
Can i used my old grub which i backedup using 
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
but how?

```
 sudo fdisk -l
```
gives me 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

please help.

---

### Post by Inxsible on 2007-06-14
grub is different than menu.
 

The menu.lst is simply the file that displays all your OS'es and you can select one of them to boot into.
 
HAve you tried hitting 'esc' or ctrl + x or ctrl + z to exit?
 
I am sorry, I am not sure what the exact command is, but those are the ones mostly used to exit.

---

### Post by reclusivemonkey on 2007-06-14
> **timo_01 said:**
> i think i messed or overwrote my grub because i get only ```
grub > 
```as the startup. with also minimal BASH like line editing is supported...
Can i used my old grub which i backedup using 
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
but how?


```
sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst
```

=]

---

### Post by timo_01 on 2007-06-14
> **Inxsible said:**
> grub is different than menu.
 

The menu.lst is simply the file that displays all your OS'es and you can select one of them to boot into.
 
HAve you tried hitting 'esc' or ctrl + x or ctrl + z to exit?
 
I am sorry, I am not sure what the exact command is, but those are the ones mostly used to exit.

i have tried esc,cltr +x,cltl+z but it jumps direct to grub> ....

when i try the command below in grub >, i get command not recognised.
```
sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst
```

how can i access the command prompt rather than grub... also with the live cd,it doesn't seem to work.

---

### Post by logos34 on 2007-06-14
> how can i access the command prompt rather than grub... also with the live cd,it doesn't seem to work.

From the live cd you have to mount your root partition first.
[B]
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
cd /mnt/ubuntu
sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst[/B]

If you have access to another machine you could download [SuperGrub]("http://supergrub.forjamari.linex.org/") utlity, burn it onto a CD and try to boot ubuntu with that.

---

