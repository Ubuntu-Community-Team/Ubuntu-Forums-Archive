---
title: "Problems with GRUB splash image and boot image"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by Antarctica on 2006-11-10
Hey, I've been following the tutorial on [www.ubuntuguide.org](www.ubuntuguide.org) for Dapper Drake.  When I went to the part about enabling a GRUB splash image ([http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up")), I followed the instructions down to every last letter.  I rebooted and instead of seeing a splash image, I get an error saying that it can't read the file.

Another problem I've encontered is the boot screen.  Again, I followed the tutorial to change the boot screen ([http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_alternate_boot_splash_screen]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_alternate_boot_splash_screen")) and I didn't like the alternate screen.  So, I ran **sudo update-alternatives --config usplash-artwork.so** and chose the original boot screen (#1).  Now, when I shut down, I'll see the original boot screen, but when I boot, I get the alternate one instead.  Can somebody help me correct these problems?

---

### Post by autocrosser on 2006-11-10
Well--as far as the Grub Splash--I have always put it after the line "End Default Options"--My menu.lst in that area looks like:

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

splashimage=(hd0,1)/boot/grub/hot-tux.xpm.gz

title        Edgy, kernel 2.6.17-10-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ht=on ro splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot


And that works fine--set-up the way the tut has it, your line would like: splashimage=(hd0,1)/boot/grub/images/hot-tux.xpm.gz

try re-editing the file like that--remove your prior edit & change it more like mine--If you have problems, post your menu.lst

As for the Usplash--use Synaptic & reinstall Usplash & the Ubuntu image that goes with it--do a search with usplash in the text field.....

---

### Post by Jimmy_r on 2006-11-11
In your /boot/grub/menu.lst you should have a line beginning with groot=
Make sure the part within parenthesis is the same as the part within parenthesis in your splash image line.
For example if your groot line says groot=(hd0,1) make sure your image line begins with splashimage=(hd0,1)

---

