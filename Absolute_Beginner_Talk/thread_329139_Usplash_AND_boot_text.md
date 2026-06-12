---
title: "Usplash AND boot text?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by wilberfan on 2007-01-01
I don't remember the scenario, but I can recall one instance where I got to see the ubuntu usplash screen AND boot text scrolling by on top of it...

It was a cool effect.

Does anyone know how to make that happen again?  :-k

---

### Post by nunomiguelmota on 2007-01-01
it is simple, just have to edit the boot kernel options, like this:

```
sudo gedit /boot/grub/menu.lst
```

search for a line like this one:

kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash vga=791

and remove the "quiet"

---

### Post by wilberfan on 2007-01-01
Oh...DUDE!   I looks so cooooooooool!  

I suspected it was the "quiet" parameter--but I didn't want to screw something up at the beginning of the new year!

Thanks...!

---

### Post by Ramses de Norre on 2007-01-01
To get better results you'll want to search for the #defoptions line in menu.lst and remove the quiet there, then run **sudo update-grub**. The quiet option will then be removed from all kernel lines and wont be added to new kernels anymore.

---

### Post by nrwilk on 2007-01-11
This is great.  It's the same behavior that I had with Dapper.  Glad to have it back.

This also, for some reason, fixed some errors that usplash would throw every time I booted up while it was poking around in my system.

Thanks!  :) 

nrwilk

---

### Post by C.J. on 2007-01-27
Nice. I really missed seeing what is going on at boot. Now I can see what it is doing when it hangs a bit at start up. Hard to diagnose blind.

Thanks.

---

### Post by nrwilk on 2007-01-27
> **C.J. said:**
> Nice. I really missed seeing what is going on at boot. Now I can see what it is doing when it hangs a bit at start up. Hard to diagnose blind.

Thanks.

You could also check your logs.  Everything that happens during bootup is logged into a file.

It should be a file called /var/log/boot

=o)

nrwilk

---

### Post by Cactus Sediento on 2007-03-02
Thanks :) Also missing those instructive lines....

Could the blue color of the fonts be changed to an ubuntu traditional one (brown or orange)?

---

### Post by mcduck on 2007-03-02
> **Cactus Sediento said:**
> Thanks :) Also missing those instructive lines....

Could the blue color of the fonts be changed to an ubuntu traditional one (brown or orange)?

Actually they are brown for me. :D

I'm using 'vga=792' as the last entry to boot in 1024x768 with 32-bit colors. I had to do that to get the virtual terminals working with my Mobility Radeon X1600.

---

### Post by Cactus Sediento on 2007-03-02
Now is brown also for me :), thanks

---

