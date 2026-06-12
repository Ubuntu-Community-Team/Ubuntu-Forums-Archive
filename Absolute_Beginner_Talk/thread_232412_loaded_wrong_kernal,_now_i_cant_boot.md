---
title: "loaded wrong kernal, now i cant boot"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by joethesmith on 2006-08-08
so to start off... Im an idiot. I took something that was working, and had to break it.

I have an AMD athlon chip and so I loaded 

sudo apt-get install linux-k7

and no i cant load anymore, on the boot screen it gets to loading mandatory drivers (I think thats it, its the 1st one) then it does nothing else.

does anyone know how i can either revert the kernal or just load a new one.

Thanks
Joe

---

### Post by Brunellus on 2006-08-08
you should be able to get to the GRUB menu screen on startup.  pick your old kernel, boot into that, then remove the new kernel with synaptic.

---

### Post by joethesmith on 2006-08-08
how do i get into the GRUB menu? because i get nothing. it seems to lock when it (ubuntu) is loading. Is there a certain keypress i can use to get into it?

---

### Post by jordilin on 2006-08-08
You can always boot from a live Cd and try to access your configuration files.

---

### Post by Tomosaur on 2006-08-08
Press Esc during bootup to show the Grub menu.

---

### Post by christhemonkey on 2006-08-08
Whilst booting, if you press esc, the GRUB menu appears before it boots into ubuntu.

It is the very previous thing, after your BIOS flashes its random crap up on the screen.

---

### Post by joethesmith on 2006-08-08
I did try to access the files using the liveCD (thats what im using now) but it wont mount the main HD that has the config files.

---

### Post by joethesmith on 2006-08-08
you guys are life savers!! Thanks a lot! 

Im off to go muck things up :D 

Joe

---

### Post by christhemonkey on 2006-08-08
Enjoy :D

---

