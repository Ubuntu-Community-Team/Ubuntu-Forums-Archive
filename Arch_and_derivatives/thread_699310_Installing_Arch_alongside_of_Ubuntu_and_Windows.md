---
title: "Installing Arch alongside of Ubuntu and Windows"
date: 2008-02-17
forum: Arch and derivatives
---

### Post by Nevon on 2008-02-17
I've done dual, and even triple booting installations before, but this is a little trickier than that. See, I have two physical harddrives. One large containing Windows, Ubuntu, and a storage partition, and another harddrive that is currently empty.
What I would like to do now is to install Arch on that second harddrive, but still use my old GRUB on harddrive number one. 

Question #1: How do I install Arch on that second harddrive without it making that harddrive the default harddrive to boot from? 

Question #2: How do I edit my GRUB so that I can go into Arch?

---

### Post by PmDematagoda on 2008-02-17
This thread has been moved to the Arch section.

---

### Post by jken146 on 2008-02-17
This isn't difficult.  Install Arch and when you get to the stage for installing GRUB, do install it, but install it on the partition that is / for Arch.  Your PC will continue to boot from Ubuntu's GRUB.

Next, boot into Ubuntu and mount your Arch partition. navigate to <arch_partition>/boot/grub/ and copy the relevant section of menu.lst to the end of the /boot/grub/menu.lst file (Ubuntu's GRUB).

The relevant section will probably look a bit like this: ```
title Arch Linux
root (hd3,6)
kernel /boot/vmlinuz26 root=/dev/sdd7 ro
initrd /boot/kernel26.img

title Arch Linux Fallback
root (hd3,6)
kernel /boot/vmlinuz26 root=/dev/sdd7 ro
initrd /boot/kernel26-fallback.img

```

---

### Post by Nevon on 2008-02-17
I see, thank you very much. Now I just need to find a printer so that I can print out any information I may need, **before** I start mucking up my system :D

---

### Post by Pumalite on 2008-02-17
Better yet; make a backup of your menu.lst before you edit:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old

---

### Post by lex1 on 2008-02-17
my son needs to use windows i have a imac dual booting with ubuntu please can some comments be made for a triple boot is it possible?

lex1

---

### Post by wolfvorkian1 on 2008-06-26
> **jken146 said:**
> This isn't difficult.  Install Arch and when you get to the stage for installing GRUB, do install it, but install it on the partition that is / for Arch.  Your PC will continue to boot from Ubuntu's GRUB.

Next, boot into Ubuntu and mount your Arch partition. navigate to <arch_partition>/boot/grub/ and copy the relevant section of menu.lst to the end of the /boot/grub/menu.lst file (Ubuntu's GRUB).

The relevant section will probably look a bit like this: ```
title Arch Linux
root (hd3,6)
kernel /boot/vmlinuz26 root=/dev/sdd7 ro
initrd /boot/kernel26.img

title Arch Linux Fallback
root (hd3,6)
kernel /boot/vmlinuz26 root=/dev/sdd7 ro
initrd /boot/kernel26-fallback.img

```


After more hours of googling than my ego wants me to admit to, I finally ran across someone who could explain how to do this in non-geek language. 

There has to be one zillion posts, maybe two, about double booting with windows and linux using one or both hard drives but this is the only one I found that has allowed me to do it with Arch on the slave drive with a linux distro on the master. 

Thank you. Mandla ought to sticky your post. Some other distros I've tried set up the dual booting automatically but naturally Arch doesn't. Setting up Arch and getting it functioning was a piece of cake compared to getting it to boot without screwing up the booting on my main distro... Lenny.

---

