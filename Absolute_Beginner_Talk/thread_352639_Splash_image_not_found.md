---
title: "Splash image not found"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by question_chick on 2007-02-03
Hi there, 

I seem to be lacking in a grub splash image. Now I know I could go out and install al manner of custom ones and it would probably fix my problem but I kinda want to stick with the original image if I could.

Ubuntu starts fine, it's just that where the stratup image should be my monitor throws a hissy fit and says it's can't display anything. So no pretty progress bar or anything, after that it all works fine again.

Any help much appreciated.

This may help too  . . . . 

psyke@Psykez-Comp:~$ sudo dpkg-reconfigure linux-image-$(uname -r)
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.17.1-10.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.17.1-10.34 was configured last, according to dpkg)
Running postinst hook /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by question_chick on 2007-02-03
Bump - Sorry just looking for an answer

---

### Post by randiroo76073 on 2007-02-03
Mine are located in either /user/shared/images/desktop-base or /user/shared/pixmaps/splash.  Does that help?

---

### Post by jaybombalous on 2007-10-27
> jasin@ubuntunetwork:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

jasin@ubuntunetwork:~$ sudo startupmanager
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

tell me, what does all this mean and how in the world can I fix it?

---

### Post by jaybombalous on 2007-10-28
bump - its been 12 hours? anyone???

---

### Post by stueycaster on 2007-10-28
Get startupmanager from Synaptic. Setting the resolution to 800x600 fixed mine. I left the color depth at 8 bits.

---

### Post by jaybombalous on 2007-10-28
Ok, I d/l'd SUM but I changed the size, maybe if i go back to default it will work. Thanks for the tip!

edit: nope, still can't find the splash image. This is strange, brand new installation on new computer and from the first boot nothing. I installed gelibs,skype, and audacious. I don't think they had anything to do with it but I could be mistaken.

---

### Post by stueycaster on 2007-10-28
You might have to experiment. In the post where I found out about it someone else had to use a different resolution. I tried to find the thread where I found out about it but couldn't. Sorry.

---

### Post by por100pre1 on 2007-10-28
Try reinstalling and reconfiguring the usplash theme:

```
sudo aptitude reinstall usplash-theme-ubuntu
```

```
sudo dpkg-reconfigure usplash-theme-ubuntu
```

Check if there are any error messages. :-k

---

### Post by jaybombalous on 2007-10-29
Well I tried this and since the reboot I can finally see whats loading in the background. But now I remember removing the splash form defoptions in menu.lst.

This is a step in the right direction, at least I have some form of visual on my screen, just not a splash as of yet.

When I do...

```
sudo update-grub
```


I still get the error, no splash image is found though. :(

---

### Post by jaybombalous on 2007-10-29
Ok, I am confirming this as a bug. It doesn't matter what resolution I use or what I put in the menu.lst file and update inintramfs. I still see no bootloader splash screen...

---

### Post by jaybombalous on 2007-10-29
now, How do I get to the page to confirm this as a bug since i can't possibly fix it. Maybe someone can use my information to track it down.

---

