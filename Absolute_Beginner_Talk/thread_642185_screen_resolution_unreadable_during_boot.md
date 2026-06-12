---
title: "screen resolution unreadable during boot"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by rexxxlo on 2007-12-16
im really confused here 

i rebooted my machine and everything seemed fine until after the bootup/bios screen gets to the part where it tells me verifying dmi pool data 

the resolution goes very big 800x600 or so and the bottom right hand corner stays anchored while the rest of the screen beyond the edge 

if i go into the bios it is like this also 

when i get to the login all is fine i can take a screen shot but if i need to i will take a picture post it  on photobucket 

i have reconfigured xorg 2 times to no avail although i have a question bout this,does nv and nvidia give the same results?
why can this not detect my card ,or monitor? and if i put this info in the xorg setup finish it and start it again, why do i have to enter it all again?

---

### Post by Pumalite on 2007-12-16
Did you try 'vesa' as the driver?

---

### Post by rexxxlo on 2007-12-16
no why ,what is the vesa driver?

i have an nvidia card 
GeForce 6100 nForce 430

should i use the vesa driver with that?

---

### Post by Pumalite on 2007-12-16
Vesa is a generic driver that allows you IN the system with decent graphics. Later you install appropriate driver.

---

### Post by rexxxlo on 2007-12-16
nice i will try that but my question is why does just a small part of boot up do this everything else is fine, just so happens to be where the errors are being posted.

---

### Post by rexxxlo on 2007-12-16
here is a picture 

[IMG]http://i232.photobucket.com/albums/ee266/psychoacoustics/IMG_1249.jpg[/IMG]

---

### Post by diatribe on 2007-12-16
you need to change your framebuffer in menu.lst to something smaller I would guess

---

### Post by Pumalite on 2007-12-16
See if configuring the xserver with NO framebuffer will do the trick.

---

### Post by philinux on 2007-12-16
Try installing and running startup-manager then choose your boot resolution.

---

### Post by diatribe on 2007-12-16
> **Pumalite said:**
> See if configuring the xserver with NO framebuffer will do the trick.

the xserver has nothing to do with the actual console resolution

---

### Post by rexxxlo on 2007-12-16
ok so its not xorg 

i scaled the screen size down with the controls on the monitor i can see all of the text it locks up during the boot  with all of the foillowing options

i checked the cd its good
i have been running memtest for about 18 min now all looks good 
have rebooted with hdd unplugged.....nothing
have started in safe graphics mode same ......nothing

its strange it seems like hard ware but i have tried 2 video cards and unplugged all hdd's

---

