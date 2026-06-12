---
title: "Ubuntu and Vista rEFIt and grub issue."
date: 2008-06-15
forum: Apple Hardware Users
---

### Post by harish_kd on 2008-06-15
I triple booted Ubuntu and vista after resizing the partitions in mac book and installing rEFIt
the order of installation is mac os x(already installed) -> Vista ->Ubuntu    ...as recommended
In the boot menu of rEFit, i get all the 3 os options but for both vista and Ubuntu , grub gets started and grub menu comes.
I want rEFIt to directly send me to vista or Ubuntu

I figured out the structure, grub is taking away both vista and Ubuntu boot loaders. If i select vista in the rEFIt menu, the grub menu comes up to select visa or Ubuntu. If i select vista, it then gives the boot process to BCD.
What i want is to direcly boot into the selected os (from rEFIt menu)without any interference.

---

### Post by Chrisj303 on 2008-06-15
You need to install your bootloader (I use LILO) to the Linux root partition.

---

### Post by cyberdork33 on 2008-06-15
yep see the multiboot link in my sig.

---

### Post by mcandre on 2008-06-15
You'll have to look into deleting just the right partitions to remove grub from booting Windows AND Ubuntu. Then you'll have to install grub again. The easy way is to reinstall Ubuntu from scratch. Follow the instructions at this [blog post]("http://mcandre.blogspot.com/2008/04/triple-booting-leopard-vista-ubuntu.html"). Just before the actual installation commences, click Advanced and specify that you want to install grub to (hda0,2) if the Linux HD is /dev/sda3, etc.

---

### Post by cyberdork33 on 2008-06-15
> **mcandre said:**
> You'll have to look into deleting just the right partitions to remove grub from booting Windows AND Ubuntu. Then you'll have to install grub again. The easy way is to reinstall Ubuntu from scratch. Follow the instructions at this [blog post]("http://mcandre.blogspot.com/2008/04/triple-booting-leopard-vista-ubuntu.html"). Just before the actual installation commences, click Advanced and specify that you want to install grub to (hda0,2) if the Linux HD is /dev/sda3, etc.
you do not need to reinstall ubuntu, just grub.

---

### Post by harish_kd on 2008-06-16
> **cyberdork33 said:**
> yep see the multiboot link in my sig.

after going through your steps, 4 partitions show up in refit menu.
1 mac os
2 linux from hd
3 windows on partition 3
4 linux on partition 4

when i select 2 ,tux is sitting at the middle of the bot screen. System doenn't boot.
 selecting 3 or 4 leads to grub menu

---

### Post by Chrisj303 on 2008-06-16
Why have you got 2 Linux partitions? - are you trying to setup a swap *partition*?

I just create 3 partitions - one for each OS - then use a swap *file*. As long as I install the bootloader to the root, then the result is exactly as you are wanting...

---

### Post by harish_kd on 2008-06-16
> **Chrisj303 said:**
> Why have you got 2 Linux partitions? - are you trying to setup a swap *partition*?

I just create 3 partitions - one for each OS - then use a swap *file*. As long as I install the bootloader to the root, then the result is exactly as you are wanting...

I'm clear that there is no swap space at all in my installation.
The 2 nd option is "boot linux from HD" which doesn't work.

Only the fourth option that appeared after installing grub is working.

i only want to know if there is any way to remove the option or just hide it atleast.

---

### Post by cyberdork33 on 2008-06-16
> **harish_kd said:**
> I'm clear that there is no swap space at all in my installation.
The 2 nd option is "boot linux from HD" which doesn't work.

Only the fourth option that appeared after installing grub is working.

i only want to know if there is any way to remove the option or just hide it atleast.Reinstalling the windows bootloader should clear it up. (i.e. FIXMBR). If not then, you must have accidently installed grub to some other partition as well.

---

### Post by harish_kd on 2008-06-17
> **cyberdork33 said:**
> Reinstalling the windows bootloader should clear it up. (i.e. FIXMBR). If not then, you must have accidently installed grub to some other partition as well.

Anyway, how to edit rEFIt menu,ie.,default, names etc..
The only thing i found is the timeout in *.conf file in refit file

---

### Post by cyberdork33 on 2008-06-17
> **harish_kd said:**
> Anyway, how to edit rEFIt menu,ie.,default, names etc..
The only thing i found is the timeout in *.conf file in refit fileyou can't edit the names, etc.

the refit.conf file allows you to set "legacyfirst" and you can replace the OS icons with whatever you like. Some of the other menu items you can hide (tools and utilities at the bottom), but i wouldn't recommend that because you might need them

---

