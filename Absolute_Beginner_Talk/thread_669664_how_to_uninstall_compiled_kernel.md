---
title: "how to uninstall compiled kernel"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by taekr on 2008-01-16
hi, 

I reinstalled ubuntu 7.1 with Live CD then complied kernel according to Master Kernel thread. [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

then, I got a problem. It doesn't detect my vedio card.. I am getting an error to open restricted drivers manager. I would like to uninstall complied kernel and retry..  

Because I do dual boot with XP, I see the older kernel version in the bootup menu ...  now I'm writing this on the older version of kernel. 

How can I uninstall the complied kernel without any trace so I can redo it? 

Thanks

---

### Post by PeterJS on 2008-01-16
> **taekr said:**
> hi, 

I reinstalled ubuntu 7.1 with Live CD then complied kernel according to Master Kernel thread. [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

then, I got a problem. It doesn't detect my vedio card.. I am getting an error to open restricted drivers manager. I would like to uninstall complied kernel and retry..  

Because I do dual boot with XP, I see the older kernel version in the bootup menu ...  now I'm writing this on the older version of kernel. 

How can I uninstall the complied kernel without any trace so I can redo it? 

Thanks

Open up the grub configuration file (/boot/gub/menu.lst) and find the section for the kernel you don't want to use, and delete it. Then go find where you put the kernel itself on disk and delete it, this step isn't as important, a compiled kernel really doesn't take up that much space.

---

### Post by taekr on 2008-01-16
> **PeterJS said:**
> Open up the grub configuration file (/boot/gub/menu.lst) and find the section for the kernel you don't want to use, and delete it. Then go find where you put the kernel itself on disk and delete it, this step isn't as important, a compiled kernel really doesn't take up that much space.

Thank you for the reply. 

Ah.. so what you are saying is go to /usr/src where the followings are listed 

linux-2.6.23
linux-headers-2.6.22-14
linux-headers-2.6.22-14-generic
linux-headers-2.6.23.12
linux-2.6.23.tar.bz2
linux-headers-2.6.23.12_386.i386.deb
linux-image-2.6.23.12_386_i386.deb

and a link file...    linux -> /usr/src/linux-2.6.23


and delete everything contains 2.6.23 

Is that right? 

go to

---

### Post by taekr on 2008-01-16
> **PeterJS said:**
> Open up the grub configuration file (/boot/gub/menu.lst) and find the section for the kernel you don't want to use, and delete it. Then go find where you put the kernel itself on disk and delete it, this step isn't as important, a compiled kernel really doesn't take up that much space.

Also, I'm on the older version of kernel. and 

when I open /boot/grub/menu.lst, it's empty. Any idea?

---

