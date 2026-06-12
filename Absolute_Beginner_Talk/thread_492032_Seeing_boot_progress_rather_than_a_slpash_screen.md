---
title: "Seeing boot progress rather than a slpash screen"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-07-04
Just a quick question, I was wondering if it is possible to view the "grub"? menu while ubuntu is loading as oppose to the logo and the progress bar.  my reason for this is i was trying to get my wireless to work using ndiswrapper and i added ndiswrapper to /etc/modules and i after i rebooted still no wireless! i have been trying to get it to work for a while now and still nothing!  then one time i put the lid down on my notebook and returned to it and it displayed all the things it was loading as ubuntu booted and then i caught a glimpse of it and it said: "ndiwswrapper failed to laod" and then i tried reading more but then the ubuntu progress bar came on with the logo.  I would like to see what else was displayed there and if there are any other things that aren't loading correctly, therefore is it possible to view this progress screen??

Thanks, Alain

---

### Post by Happy_Man on 2007-07-04
Sure, once it's booted, go to a Terminal and use these commands: ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.bak
gksudo gedit /boot/grub/menu.lst
```

Scroll down to the listing with the kernel that YOU boot from. Somewhere there, it will say "quiet" "splash". Delete those words, save, and reboot. It should now show the boot menu dialog.

---

