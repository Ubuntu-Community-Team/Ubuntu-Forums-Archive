---
title: "Is all of this really needed?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Zaosyn on 2007-04-21
HI there :) Today I installed 7.04, but during the installation ( at the very end ) my PC shutted down, however I'm using 7.04 now. 

But what boggles me is when I restart I get my dual boot screen. Is all of these really necessary? 

I understand if it is, it's really no problem for me, I'm just curious on why so many.

If it matters I've had to upgrade from 6.06 to 6.10, to 7.04. 

[img][[IMG]http://img153.imageshack.us/img153/3010/pic0421074sf9.jpg[/IMG]](http://imageshack.us)

As you can see all the extra boot options, and at the very bottom Windows XP professional is there.

---

### Post by ComplexNumber on 2007-04-21
wow! you've certainly upgraded quite a few times...to say the least :lolflag:. 
i would get rid of some of your kernels, although its not absolutely necessary. also, be careful about what  you uninstall. if you're uncertain, leave it like it is.

---

### Post by Happy_Man on 2007-04-21
Well, every major OS update for Linux usually includes a new kernel. This is roughly analogous to service packs for Windows. All those listings there are kernels for Ubuntu, for each version. They don't harm your computer if they're there, and if they're annoying you, you can always delete their listings on the GRUB screen. 

```
gksudo gedit /boot/grub/menu.lst
```

But be careful not to delete all of them! Then you wouldn't be able to get into Ubuntu at all. :O

---

### Post by Zaosyn on 2007-04-21
I just started using Ubuntu, and I'm fine with the way it is. I was just curious if everyone's were like this X] 

Now to go and enjoy installing plugins!

---

### Post by jtraub on 2007-04-21
You can delete that entries in file /boot/grub/menu.lst and kernel/initrd files from /boot

---

### Post by milton1 on 2007-04-21
Not necessary, no. The old kernel is left for two reasons: one, in case the new one does not work and two, because you are running the old kernel when you install the new one. Try out the new one for a while. If it works, uninstall the old ones. Easiest way (my opinion) to do this is search in synaptic/adept for the kernel version number (2.6.15, etc), and choose 'remove'

---

### Post by chakkaradeep on 2007-04-21
When a Kernel upgrade happens, to make sure that you dont fall in a trap where the new kernel does not boot, the old kernel is kept as is and thats the reason you get them there. If at all after kernel upgrade if the new kernel fails, you can very well choose other options :)

---

### Post by bulldog on 2007-04-21
Maybe a simple ```
sudo update-grub
``` will remove the Edgy kernels,but if they still exist in the boot folder,you have to uninstall them with synaptic.
Do a search on linux-image but ** don't remove your current kernel**

It's recommended to leave two kernels so you can fall back in case of failure.
But in your case you only have one new kernel which is the one at the top.

To find out the current kernel```
uname -a
``` in a terminal,this one you shouldn't remove :)

---

