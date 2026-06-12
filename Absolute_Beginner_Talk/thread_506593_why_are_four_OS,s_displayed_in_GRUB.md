---
title: "why are four OS,s displayed in GRUB"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by tommy2c on 2007-07-21
HI,

Is it normal to have GRUB display four installs of Ubuntu?

1.   Ubuntu kernel 2.6.20-16 (generic)
2.   Ubuntu kernel 2.6.20-16 (recovery mode)
3.   Ubuntu kernel 2.6.20-15 (generic)
4.   Ubuntu kernel 2.6.20-15 (recovery mode)

and added
5.   Ubuntu memtest86+

GRUB auto boots well to Ubuntu kernel 2.6.20-16 (generic),  and when I manually boot to the 2.6.20-15 kernel the only difference seems to to screen resolution.

Is this config normal?

Also, I ran the memtest86+ utill., it really does not work well,  does it need to be here at boot menu?

The install was a clean install giving total use of HD.

Thanks

---

### Post by por100pre1 on 2007-07-21
3 and 4 are the original kernel of the Ubuntu installation, 1 and 2 are the updated kernel (an important update) 5 is a tool present in the installation. **[COLOR="Red"]Everything there is normal.[/COLOR]**

---

### Post by pyros on 2007-07-21
Yep, that's normal. the first four entries are all for different ways of starting ubuntu. Every time your kernel updates, you will have new entries there. they don't hurt anything, but they can be removed if it bothers you.

---

### Post by Tux Aubrey on 2007-07-21
Yes - all OK.  They are not different installs - just different ways of starting Ubuntu and different kernels.  These are important if something breaks!  Recovery mode is a command line interface.

If you want to tweak the grub menu (not advised at this early stage if things are working!) or just want to explore the many options available, there is a heavily commented config file in the boot/grub directory called menu.lst that you can open and read in gedit or another text editor.  The file is read-only so you can't accidentally break it.

---

### Post by kyphi on 2007-07-21
The purpose of showing the older and the newer is so that you can be sure that everything will work OK with your equipment and configuration.

You must have access to boot a kernel in normal mode as well as safe mode.  The memory test makes up the trio.

You could comment the mem test out.

You can edit your bootmenu list to only show one kernel entry if you so wish but this would not take effect until the next kernel update.  Until then you are stuck with it.

---

### Post by tommy2c on 2007-07-21
Hi,

Thank you for you quick replies! :)

I wanted to ask about the 4 installs on GRUB because the boot time seems widened looking for them.?  

Thanks

---

### Post by kyphi on 2007-07-21
> I wanted to ask about the 4 installs on GRUB because the boot time seems widened looking for them.? 

You can shorten the boot time in the menu.lst file if you think that your reaction time is up to it.

---

### Post by alienexplorers on 2007-07-21
You can always comment them out by putting a pound (#) mark if you don't want them in your grub menu.
> #title		Ubuntu, kernel 2.6.15-26-386
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-26-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.15-26-386

---

### Post by tommy2c on 2007-07-21
> **kyphi said:**
> You can shorten the boot time in the menu.lst file if you think that your reaction time is up to it.

Hi kyphi,

Thanks for your info.  I'm not too sure where to find the menu.lst file you mention.  Is it in GRUB?  Is there a tutorial for the use of GRUB so that I might stop bugging others for info I can easily find myself?

Thanks

---

### Post by Nekiruhs on 2007-07-21
> **tommy2c said:**
> Hi kyphi,

Thanks for your info.  I'm not too sure where to find the menu.lst file you mention.  Is it in GRUB?  Is there a tutorial for the use of GRUB so that I might stop bugging others for info I can easily find myself?

Thanks
Just do a ```
gksudo gedit /boot/grub/menu.lst
```That'll open gedit to read/write menu.lst

---

### Post by tommy2c on 2007-07-21
> **Nekiruhs said:**
> Just do a ```
gksudo gedit /boot/grub/menu.lst
```That'll open gedit to read/write menu.lst

Thank you Nekiruhs,

I think this is the solution!

---

### Post by tommy2c on 2007-07-21
Thank you all for you posts.

Please end thread now.

---

