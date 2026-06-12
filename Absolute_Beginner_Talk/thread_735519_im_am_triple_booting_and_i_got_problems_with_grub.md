---
title: "im am triple booting and i got problems with grub"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by boboyo4 on 2008-03-25
yesterday, ive installed Sabayon Linux on my sda4
sda1 : win vista
sda2 : ubuntu
sda3 : swap partition 
sda4 : sabayon

when i was installing sabayon, i didnt want to install grub because i already wave it 
but now, i cant go on sabayon

does anyome know how to add an OS on grub because ive tried this

title Sabayon
root (hd0,3)
makeactive (i tried it without this too)
chainloader +1

whit this, i get an error message that looks like this
error 13 unsupported something and incapable to lod or something
when i put the root (hd0,4), it says no such partition

does anyone have sabayon installed or can someone help me?

---

### Post by herbster on 2008-03-25
```
# Sabayon
title  Sabayon
root   (hd0,3)
kernel /boot/vmlinuz26 root=/dev/sda4 ro
initrd /boot/kernel26.img
```

Try that? I don't use Ubuntu so the kernel image could differ, someone can chime in.

---

### Post by boboyo4 on 2008-03-25
nop
didnt work
but now, the error message has changed
now it says
error15 file not found

---

### Post by oldos2er on 2008-03-25
Change the kernel and initrd lines to whatever they are in Sabayon's /boot directory.

---

### Post by herbster on 2008-03-25
Yeah whoops, forgot he's using Sabayon, haha.

---

### Post by boboyo4 on 2008-03-25
ok ill try it but ill have to search a bit

---

### Post by louieb on 2008-03-25
try the configfile option. Thats  how I do it most of the time.  The other option is to chainload.   

```

title  Test Linux configfile on (hd0,3)    
       configfile (hd0,3)/boot/grub/menu.lst      

```More here on configfile and chainload options.
[IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by boboyo4 on 2008-03-25
this is what ive found and it doesnt work 

kernel /boot/kernel-genkernel-x86-2.6.18-gentoo-r5 root=/dev/ram0 ramdisk=8192 real_root=/dev/hdb3 quiet init=/linuxrc doslowusb splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1
initrd /boot/initramfs-genkernel-x86-2.6.18-gentoo-r5

---

### Post by boboyo4 on 2008-03-25
> **louieb said:**
> try the configfile option. Thats  how I do it most of the time.  The other option is to chainload.   

```

title  Test Linux configfile on (hd0,3)    
       configfile (hd0,3)/boot/grub/menu.lst      

```More here on configfile and chainload options.
[IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")
to louieb
title  Test Linux configfile on (hd0,3)    
       configfile (hd0,3)/boot/grub/menu.lst
is that all i have to do or i just replace chainload+1 with what you gave me

---

### Post by boboyo4 on 2008-03-25
it didnt work either

---

### Post by louieb on 2008-03-25
Replace everything below the title line with the configfile statment.
What this does is load the 2nd distros grub configuration file. 
The code I gave you should work as is.

Look at the page I linked to and search for **configfile.  **Herman describes it in much more detail. Good Luck.

---

### Post by boboyo4 on 2008-03-25
when i was installin sabayon, my friend told me to not install grub becaus e i didnt need it cuz i already have it
i think that thats why it doesnt work

---

### Post by boboyo4 on 2008-03-25
ive searched the net and the forums and i got 2 choices left (if you cant help me)

1-install supergrub
or
2-reinstall sabayon (with grub this time)

---

### Post by odiseo77 on 2008-03-25
> **boboyo4 said:**
> ive searched the net and the forums and i got 2 choices left (if you cant help me)

1-install supergrub
or
2-reinstall sabayon (with grub this time)

There's no need to do all that stuff; you can chroot sabayon and install grub into sabayon's '/' partition:

```
sudo -s
mkdir /mnt/sabayon
mount /dev/sda4 /mnt/sabayon
chroot /mnt/sabayon /bin/bash
grub-install /dev/sda4
exit
```

If the grub-install command doesn't work you can substitute it with:

```
grub-install (hd0,3)
```

It should create a menu.lst (or grub.conf) inside sabayon's /boot or /boot/grub. Now all you have to do is to copy the necessary lines from sabayon's menu.lst into ubuntu's menu.lst.

However, I think louieb's method might be a bit cleaner.

---

### Post by boboyo4 on 2008-03-25
> **odiseo77 said:**
> There's no need to do all that stuff; you can chroot sabayon and install grub into sabayon's '/' partition:

```
sudo -s
mkdir /mnt/sabayon
mount /dev/sda4 /mnt/sabayon
chroot /mnt/sabayon /bin/bash
grub-install /dev/sda4
exit
```

If the grub-install command doesn't work you can substitute it with:

```
grub-install (hd0,3)
```

It should create a menu.lst (or grub.conf) inside sabayon's /boot or /boot/grub. Now all you have to do is to copy the necessary lines from sabayon's menu.lst into ubuntu's menu.lst.

However, I think louieb's method might be a bit cleaner.
when i get to the grub-install part, this is what happens
grub-install /dev/sda4
/dev/root: Not found or not a block device.

---

### Post by boboyo4 on 2008-03-25
> **boboyo4 said:**
> when i get to the grub-install part, this is what happens
grub-install /dev/sda4
/dev/root: Not found or not a block device.
when i tried grub-install (hd0,3), it doesnt work either 
grub-install (hd0,3)
bash: syntax error near unexpected token `hd0,3'

---

### Post by boboyo4 on 2008-03-25
now i can see my sabayon partition called /mnt/sabayon
i can see grub but everything in grub (in the sabayon part) is fine except menu.lst that i tried to rename by grub.conf and it is still the same : when i click on it, it says
This link can't be used, because its target "/mnt/sabayon/boot/grub/grub.conf" doesn't exist. and theres cancel and move to trash

---

### Post by odiseo77 on 2008-03-25
You shouldn't rename menu.lst to grub.conf; if it's a file named menu.lst there, then you should leave it as it is. Now, could you post the output of the following commands?:

```
ls -l /mnt/sabayon/boot
ls -l /mnt/sabayon/boot/grub
```

(this should help us to find where's the menu.lst file, or if it's there at all).

---

### Post by boboyo4 on 2008-03-25
> **odiseo77 said:**
> You shouldn't rename menu.lst to grub.conf; if it's a file named menu.lst there, then you should leave it as it is. Now, could you post the output of the following commands?:

```
ls -l /mnt/sabayon/boot
ls -l /mnt/sabayon/boot/grub
```

(this should help us to find where's the menu.lst file, or if it's there at all).
boris@boris-laptop:~$ ls -l /mnt/sabayon/boot
total 9760
lrwxrwxrwx 1 root root       1 2008-03-24 15:28 boot -> .
drwxr-xr-x 2 root root    4096 2008-03-25 23:46 grub
-rw-r--r-- 1 root root 3982397 2007-09-02 18:42 initramfs-genkernel-x86-2.6.22-sabayon
-rw-r--r-- 1 root root 4349168 2007-09-02 18:23 kernel-genkernel-x86-2.6.22-sabayon
-rw-r--r-- 1 root root 1633142 2007-09-02 18:23 System.map-genkernel-x86-2.6.22-sabayon
boris@boris-laptop:~$ ls -l /mnt/sabayon/boot/grub

---

### Post by odiseo77 on 2008-03-26
Well, too bad there's no menu.lst there. Try adding the following lines at the end of your Ubuntu's menu.lst (be careful not to delete the other lines, just add  these ones):

```
# Sabayon
title  Sabayon
root   (hd0,3)
kernel /boot/kernel-genkernel-x86-2.6.22-sabayon root=/dev/sda4 ro
initrd /boot/initramfs-genkernel-x86-2.6.22-sabayon
```

Hope it works.

---

### Post by dummyhead3 on 2008-03-26
boboyo4 is gone (he's on a trip) for the moment so he asked me to inform you:

Sabayon boot works grea nowt. thanks a bunch!

---

### Post by odiseo77 on 2008-03-26
Good. Glad to know it worked :)

---

### Post by gangsterhead3 on 2008-03-29
boboyo4 says that sabayon is very bad.
he says that when sabayon finishes loading he has a white screen and he tought it was because if grub or something so he moved grub from boot in ubuntu and he tried to reinstall sabayon but with grub this time.
sabayon still had a white screen and all he could see is his cursor.
he got very mad so he deletedhis sabayon partition and he broke the cd because its been a week hes tryin to install it and it had too many problems.

then i tried to move grub back in the boot folder but grub didnt work!
so he reinstalled ubuntu and now he has alot of problems with his wireless connections.

he says thank you to odiseo for helping him

i got 1 thing to tell you 
DONT INSTALL SABAYON!!!!

---

