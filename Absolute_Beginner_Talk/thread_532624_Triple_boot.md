---
title: "Triple boot?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by de_battre on 2007-08-22
Hi, i currently have a 60 gig HD with XP and ubuntu installed. I would like to try Mandriva linux because of an ongoing problem i am having in ubuntu. Is it possible to have a system with the three OS's on it where i have the option of choosing which one i would like to boot into each time i start up? If it is possible, will i need to lay any groundwork for resizing my HD partitions before i try and install mandriva, or will the installer take care of it all?

Thanks

---

### Post by de_battre on 2007-08-23
bump

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-23
you could do this 
i was considering it my self but you may wanna look into something like vmware
kuss a hard drive can only have 4 primary partions you could make afew extended partions and then have 2 secondary partions in each extended part

um but you dont need that

you have windows 1 part
you have ubuntu 2 part 
you have 3rd linux op 3 part
and you have your swap 4 part 
so you can do this no problem and when you install your 3 os it should take care of the grub configure for you so dont worry about that unless it messes up

---

### Post by glotz on 2007-08-23
It is definitely possible. I'm not familiar with the mandriva installer. Maybe you should ask at some mandriva forum. You could also use gparted (in the repos or on your Ubuntu CD) to partition the drives as you wish before hand. Usually GRUB is pretty decent in detecting other existing operating systems and listing them in the startup menu.

---

### Post by de_battre on 2007-08-23
Excellent, thanks guys.

---

### Post by bodhi.zazen on 2007-08-23
Triple booting (or more) is not much harder then dual booting.

Mainly it is a matter of making the space (use a live CD  to partition). You can share swap between distro's or even between Linux/BSD.

As a part of the install you will configure grub.

The file is /boot/rub/menu.lst (that is a small "L" and not a 1 )

The problem is that with kernel upgrades you may need to configure that file yourself.

You can get around this by chainloading (in which case you install grub to each root partition and chainload from the MBR) or by sharing a /boot partition.

HTH

---

### Post by de_battre on 2007-08-23
> **bodhi.zazen said:**
> Triple booting (or more) is not much harder then dual booting.

Mainly it is a matter of making the space (use a live CD  to partition). You can share swap between distro's or even between Linux/BSD.

As a part of the install you will configure grub.

The file is /boot/rub/menu.lst (that is a small "L" and not a 1 )

The problem is that with kernel upgrades you may need to configure that file yourself.

You can get around this by chainloading (in which case you install grub to each root partition and chainload from the MBR) or by sharing a /boot partition.

HTH

I struggle a little bit with terminal and doing command line stuff. I assume most linux distros have a graphical installer interface, so will the resizing if partitions be similar to how it was when setting up ubuntu? Which is the swap partition? Presently when i open 'computer' i see my dvd drive, a 28.5 gig volume, filesystem, and recovery. Is one of these the swap partition?  Is an installer likely to recognise it, if it is?

---

### Post by bodhi.zazen on 2007-08-23
> **de_battre said:**
> I struggle a little bit with terminal and doing command line stuff. I assume most linux distros have a graphical installer interface, so will the resizing if partitions be similar to how it was when setting up ubuntu? Which is the swap partition? Presently when i open 'computer' i see my dvd drive, a 28.5 gig volume, filesystem, and recovery. Is one of these the swap partition?  Is an installer likely to recognise it, if it is?

Yep, most distro's are gui orieted these days, and Mandriva is known for that so you should be just fine.

You can look at your partitions with gparted or list them in a terminal with :```
sudo fdisk -l
```that is a small "L" and not a 1.

If you run into problems, let us know and we will help, but it is fairly straight forward and very similar to installing ubuntu.

---

### Post by LaRoza on 2007-08-23
I have a computer with one HD, and 10 OS's, including 1 Windows, Linux, *nix.

It is easist to prepare your hard disk with GParted, then install them individually. If you install Ubuntu last, the other OS's will be added to Grub, no fiddling.

---

