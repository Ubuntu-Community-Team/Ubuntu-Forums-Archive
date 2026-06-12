---
title: "hanging on the bootscreen"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Gothicpie on 2008-03-03
O.k

I am trying to install ubuntu on my acer 7520, i'm a total beginner  

so far i have had problem after problem, but have managed to solve them with internet searches, but now I'm stumped  

at first it was hanging on the boot screen  and dropping to busybox , i managed to fix that with all_generic_ide

then i was having problems with the graphics drivers, but after a quick search i realized the reason it could not update was because i had not ticked any of the things for it to search for, i'm sorry i dont know what its called....

but anyway, the problem seemed to solve its self, it downloaded and installed the nvidia driver, then it needed a restart 

i restarted it, only to find it was hanging on the boot screen again, only this time, adding  all_generic_ide does not seem to fix it, so what can i do now?

---

### Post by glennric on 2008-03-03
What are you talking about with adding all_generic_ide?  Adding that where?

---

### Post by PmDematagoda on 2008-03-03
Boot Ubuntu in Recovery Mode and then reconfigure the X-Server to it's defaults using:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
after that is done reboot Ubuntu using:-
```
sudo restart
```
See if that allows you to reach a GUI again.

Also, what VGA card do you have?

---

### Post by PmDematagoda on 2008-03-03
> **glennric said:**
> What are you talking about with adding all_generic_ide?  Adding that where?

Adding it as a parameter on the GRUB entry for Ubuntu.

---

### Post by glennric on 2008-03-03
> **PmDematagoda said:**
> Adding it as a parameter on the GRUB entry for Ubuntu.

If that is the case, then he is having an issue with modules and the kernel.  Having him reconfigure the xserver won't help.  

Gothicpie:
Most likely your initrd image is messed up.  You should try
```
sudo update-initramfs -u
```

---

### Post by PmDematagoda on 2008-03-03
> then i was having problems with the graphics drivers, but after a quick search i realized the reason it could not update was because i had not ticked any of the things for it to search for, i'm sorry i dont know what its called....

but anyway, the problem seemed to solve its self, it downloaded and installed the nvidia driver, then it needed a restart

i restarted it, only to find it was hanging on the boot screen again
I am sorry but perhaps you haven't read this part? It clearly shows that the OP faced the problem of a blank screen again after installing the Nvidia driver package, since this behaviour is true of an incorrectly setup X-Server or driver that is why I suggested that he reconfigure the X-Server back to defaults.

---

### Post by glennric on 2008-03-03
> **PmDematagoda said:**
> I am sorry but perhaps you haven't read this part? It clearly shows that the OP faced the problem of a blank screen again after installing the Nvidia driver package, since this behaviour is true of an incorrectly setup X-Server or driver that is why I suggested that he reconfigure the X-Server back to defaults.

Oh, I see.  I have never seen a "blank" screen after updating or installing Nvidia drivers.  I have many times seen the xserver not restart and end up at a console (which is not a blank screen).  I have however seen a blank screen many times when the initrd image is messed up.  I also may have been confused by the "busybox" terminoligy.  I think he really means the console.  Busybox is something else entirely.  If you really are put into a busybox environment you can not run "sudo" anything.  It is not a real bash shell even.

---

### Post by Gothicpie on 2008-03-03
Wow, impressively fast reply/s

i am waiting for it to boot in Recovery Mode, then i will try your suggestion.

this laptop has a  nVidia Geforce 7000m in it

---

### Post by Gothicpie on 2008-03-03
oookkkkaaaayyy....

i have never booted in recovery mode before, but i'm guessing it should not do this

gets as far as

[      7.66400] uniform CD-ROM driver revision:3.20

hangs for ages, then i get 

then i get 

              Check root= bootarg cat /proc/cmdline
              or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/1e294579-35a9-4e5c-9206-565bbee6e082 does not exist. dropping to a shell!

and then i drops back to busy box

---

### Post by glennric on 2008-03-03
First of all quit calling it a "busy box."  That is not what it is.  It is a console.  Does it say anywhere that it is a busybox?  If you are dropped to a busybox you will literally be told that it is a busybox.  

That being said, it appears that your fstab is messed up or you have corrupt partitions on your harddrive.  Hopefully the former.  Post the output of
```
ls -l /dev/disk/by-uuid
```
and the output of 
```
sudo fdisk -l
```

---

### Post by Gothicpie on 2008-03-03
it says "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) built in shell (ash)" 

i just assumed it was called busybox, I apologize 

and as i said, i am a total beginner, you will have to tell me where to input both of the codes you have just listed, neither will work from here, I'm assuming there is another place i can enter them?

---

### Post by glennric on 2008-03-03
> **Gothicpie said:**
> it says "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) built in shell (ash)" 

i just assumed it was called busybox, I apologize 

and as i said, i am a total beginner, you will have to tell me where to input both of the codes you have just listed, neither will work from here, I'm assuming there is another place i can enter them?

Oh crap.  You really are at a busybox.  That means more trouble than you think.  First of all you will not be able to boot from grub (unless another option in your grub menu works and doesn't take you to a busybox).  So you will have to boot to a live cd and try to fix things from there.

---

### Post by glennric on 2008-03-03
By the way, the busybox is a shell and you can do some things from there, but only a few things.  You can try to fix things from there, but the ash shell is not very friendly.

---

### Post by Gothicpie on 2008-03-03
both the options i have dump me at this busy box, 

and my discs are all locked in with my brother, so unless you can talk me through fixing it from here, i will have to put it away and try again tomorrow

---

### Post by glennric on 2008-03-03
You can try to run "sudo update-initramfs -u" from the busy box command line, but I don't think it will work.

---

### Post by glennric on 2008-03-03
You could also try to get the information I asked for before
"ls -l /dev/disk/by-uuid" and "sudo fdisk -l".  It would also be useful to have the output of "cat /etc/fstab"

---

