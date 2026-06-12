---
title: "Change GRUB on /boot to MBR"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by kpkeerthi on 2007-12-26
I've have Vista installed alongside Linux. I'm not using it so I thought I'll get rid of it (Vista that is) and put my HD space to a better use.

**My setup:**
Vista is in /dev/sda1 and linux in /dev/sda2. MBR has Vista Boot Loader. GRUB is installed on to /boot (/dev/sda2). So my boot sequence is** MBR -> Vista BootLoader -> GRUB -> Linux**.

I know how to install GRUB onto MBR but if I do this with my setup, the boot sequence would change to **MBR -> GRUB -> GRUB -> Linux**. In other words, I'm afraid that I would end up seeing GRUB twice during boot up. 

I want **MBR -> Vista BootLoader -> GRUB -> Linux** changed to **MBR -> GRUB -> Linux**.

---

### Post by LaRoza on 2007-12-26
Can you just overwrite Vista with anothe Ubuntu install? 

Then you could transfer all files and settings to the new install (copy your home directory) and install the programs you use.

Then after everything is up, you can get rid of the original installation, and use that for data or something.

---

### Post by kpkeerthi on 2007-12-26
> **LaRoza said:**
> Can you just overwrite Vista with anothe Ubuntu install? 

Then you could transfer all files and settings to the new install (copy your home directory) and install the programs you use.

Then after everything is up, you can get rid of the original installation, and use that for data or something.

Thanks. That works. But I would like to keep that as a last resort if nothing else works.

---

### Post by LaRoza on 2007-12-26
> **kpkeerthi said:**
> Thanks. That works. But I would like to keep that as a last resort if nothing else works.

Your set up would be very difficult to alter. I wouldn't even try altering it that drastically. Sorry I couldn't be more useful.

---

### Post by kpkeerthi on 2007-12-26
If I reinstall GRUB onto MBR, does GRUB really appear twice during the boot sequence (since I already have GRUB installed in /boot partion)? How do get rid of the one I have in /boot?

---

### Post by LaRoza on 2007-12-26
> **kpkeerthi said:**
> If I reinstall GRUB onto MBR, does GRUB really appear twice during the boot sequence (since I already have GRUB installed in /boot partion)? How do get rid of the one I have in /boot?

I don't know. Sorry.

---

### Post by meierfra on 2007-12-26
Just install grub to the MBR and you will be all set. (grub  will not look at the boot sector of sda2, so  the grub menu won't appear twice)

To install grub to the MBR:


sudo grub
root (hd0,1)
setup (hd0)
quit

---

### Post by kpkeerthi on 2007-12-26
> **meierfra said:**
> Just install grub to the MBR and you will be all set. (grub  will not look at the boot sector of sda2, so  the grub menu won't appear twice)


Thanks. Thats what I found after a little more research (thanks to fedora forums).

---

