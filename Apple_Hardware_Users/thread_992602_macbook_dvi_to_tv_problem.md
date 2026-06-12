---
title: "macbook dvi to tv problem"
date: 2008-11-24
forum: Apple Hardware Users
---

### Post by jestanuff on 2008-11-24
my mac has a mini dvi out. I have the adapter to the tv but can't make it work. I'm running 8.04 on a older macbook.i installed urandr and tried the different settings but nothing works. any one make this work?:confused:

---

### Post by justdave72 on 2008-12-15
The Mac Mini thinks the TV out and the DVI are the same thing (even though they support different resolutions) and will detect both if the TV out is active.  This confuses things greatly, of course.  The solution is to disable the DVI port when you plan to use the TV-out.  I had to do this with a Mac Mini I had hooked up to an older TV a while back.  Unfortunately I don't remember the exact syntax (the Mini has moved to a TV that has HDMI so I'm using the actual DVI port now and said section has been removed from my config) but you had to add a Monitor section to xorg.conf with a device name of "TMDS-1" and Option "Ignore" "True" or something like that.  Perhaps with that clue someone else will come along and share the correct syntax. :)

---

### Post by cyberdork33 on 2008-12-15
> **jestanuff said:**
> my mac has a mini dvi out. I have the adapter to the tv but can't make it work. I'm running 8.04 on a older macbook.i installed urandr and tried the different settings but nothing works. any one make this work?:confused:
More information would be helpful.

What are you converting the DVI output to for your TV? What does "can't make it work" mean? What have you tried to do? What is the result? Is the TV screen just blank? does it flicker? Does the Macbook indicate that another display is connected?

---

### Post by jestanuff on 2008-12-15
it's been days since i tried. when i try to use the dvi out on My MACBOOK (the only xternal tv/monitor connection) i get a flicker on the tv with the svideo and the avi? stereo jack . i sure if i find the right setting it'll work. some other threads said to try uRander(or somethang like that) i have that installed but being a noob i probly didn't use it right. sooooooooooo any suggestions?

---

