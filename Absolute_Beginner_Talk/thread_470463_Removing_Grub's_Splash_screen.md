---
title: "Removing Grub's Splash screen"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by avanrens on 2007-06-11
I would like to remove the splash on boot as Kernel 2.6 20-15 won't boot and I need to see were it gets to during the boot process.

---

### Post by ramjet_1953 on 2007-06-11
What I think you really need to do here is to modify your[COLOR="Blue"] /boot/grub/menu.lst[/COLOR] file.

If you open the file and scroll down past all of the #'s to "end of default options", you will see will see a line that starts with [COLOR="Blue"]kernel[/COLOR]

In that line, you will see the word [COLOR="Blue"]quiet[/COLOR].

Carefully delete it and save the file.

When next you boot, you will be in verbose mode and what is going on during boot-up will be displayed.

Note: to modify your /boot/grub/menu.lts file requires you to edit it in [COLOR="Blue"]sudo mode[/COLOR].

Regards,
Roger :cool:

---

### Post by Tux Aubrey on 2007-06-11
<Edit> the above is correct, but this solution is a temporary way to do the same thing.</edit>

I _think_ what you need to do is edit the kernel line when the grub menu screen appears (select the boot option you want and press "e" instead of enter) there will be a couple of lines available to edit - select the one that refers to the kernel, use the arrow keys to go to the end of that line and delete the term "quiet splash".

exit and "b" for boot.

This is not permanent, just for the current session - next time you boot you would need to edit it again.  

Let us know if this works.

Do you have a nVidia card by any chance?  That's the usual cause of kernel update failures for me.

---

### Post by ageilers on 2007-06-11
Edit the /boot/grub/menu.lst file.  Look for the kernel line and remove the "quiet splash" part or comment it out with a # before it.

Boot to recovery.

```
pico /boot/grub/menu.lst
```
Arrow down to the line and add **#**:
```
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=85b3a900-bc8a-4988-a0dc-7cf9e3883304 ro #quiet splash
```
press **Crtl+x**  then **y** and **enter**. 

Or edit from Live CD.

---

### Post by avanrens on 2007-06-11
I have a nVIDIA chip set, the system boots fine pre 2.6 20-12 Kernel I guess I'll have to use the old Kernel until a fix for the nVIDIA chip set comes out.

---

### Post by Tux Aubrey on 2007-06-11
The last time this happened to me, I was able to boot to the command line with the new kernel and do:

```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r`
```

and all was well.

can't hurt to try it.

---

