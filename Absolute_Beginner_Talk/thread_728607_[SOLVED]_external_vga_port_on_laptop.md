---
title: "[SOLVED] external vga port on laptop"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by k33bz on 2008-03-19
I have an Acer 3680, running Fiesty Fawn. I have an external vga port for monitos lcd projector screens. I plugged it into my monitor and my monitor doesnt receive the signal. Is there a driver I am missing for this to work?

---

### Post by joe.turion64x2 on 2008-03-19
> **k33bz said:**
> I have an Acer 3680, running Fiesty Fawn. I have an external vga port for monitos lcd projector screens. I plugged it into my monitor and my monitor doesnt receive the signal. Is there a driver I am missing for this to work?

Did you try the usual key combination (Fn + F5)?

According to Intel's site the 950 video card your machine supports dual monitors and as far as I know drivers are not needed for Intel cards.

Good luck
Joe.

---

### Post by k33bz on 2008-03-19
Actually, honestly, no, I did not try that till you mentioned it, but with out avail, it did not work, :(

---

### Post by k33bz on 2008-03-20
ok, i got it, i had to reboot for it to go into to dual mode, but i cant toggle with Fn+F5, wont work for some reason, also lost my resolution of 1280X800

---

### Post by jordanmthomas on 2008-03-20
> **k33bz said:**
> ok, i got it, i had to reboot for it to go into to dual mode, but i cant toggle with Fn+F5, wont work for some reason, also lost my resolution of 1280X800

I think that by default it goes into clone mode (ie you see the same thing on both screens)
Unless your external monitor supports 1280x800, you won't get 1280x800.  

To properly set it up, you will want to reconfigure your /etc/X11/xorg.conf  
This process should be pretty well documented out there.  I'm not exactly sure of what you'd need to do, so I will leave it to you or someone else to find it.

---

### Post by kevin11951 on 2008-03-20
> **k33bz said:**
> ok, i got it, i had to reboot for it to go into to dual mode, but i cant toggle with Fn+F5, wont work for some reason, also lost my resolution of 1280X800

by the way, its Fn + F8! 

after you hit that go to System > Preferences > Screen Resolution. 

select the best screen resolution for the EXTERNAL screen.

 then when your done unplug it, then hit Fn+F8 again and 

Change the screen resolution back to 1280x800 or whatever your default is.

---

### Post by k33bz on 2008-03-20
> **kevin11951 said:**
> by the way, its Fn + F8! 

after you hit that go to System > Preferences > Screen Resolution. 

select the best screen resolution for the EXTERNAL screen.

 then when your done unplug it, then hit Fn+F8 again and 

Change the screen resolution back to 1280x800 or whatever your default is.

actually, according to my laptop Fn+F8 is to mute or unmute my sound, and that works, Fn+F5 is the one that is suppose to control my external screen, which it isnt working.

---

### Post by k33bz on 2008-03-20
By the way, when I said I had lost my 1280X800 resolution, I meant I had lost it completly, it is not in the choices to choose no more in my screen resolution screen.  And I know my external monitor supports it, cause it is the resolution I had it set to with my desktop.

---

### Post by k33bz on 2008-03-24
bump

---

