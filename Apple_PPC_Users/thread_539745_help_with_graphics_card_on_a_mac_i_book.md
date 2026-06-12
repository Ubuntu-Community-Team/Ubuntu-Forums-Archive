---
title: "help with graphics card on a mac i book"
date: 2007-08-31
forum: Apple PPC Users
---

### Post by jacob01 on 2007-08-31
a buddy of mine has a mac ibook that he got and after about 3 monthes and alot of tinckering it wont boot  he says, "it goes into a screen were it shows the mac sign and makes the start up noise but then goes into a black screen"

to me it sounds like it is posting or what ever mac calls it but woun't load mac os x, sound right?

could it be bad hard drive/

and i was wondering if i could get a ubuntu ppc cd will boot?

i am down loading the cd iso for ppc and was wondering weather there is a boot menu?

i think it is "c" but not sure

also i think it has an ati radon mobility radon 7500c but not sure.

how would i get the drivers for it. would they be in the repos or could i be able to get it through the restricted drivers manager

this mac was from a school so i don't know if there is any pass word protection for accessing the rom

ill be back at school on tuesday so i will let you know what happened.
im totally lost when it comes to macs so if some one can help out just a bit i would be glad

oh yea specs
hmm

ok ppc 1.5 cpu upgraded from a 800mhz ? no idea what he did he likes t tinker around with stuff
and ram i have no idea i am pretty sure 256 128 internal and a 128 card but he commented that it has 1.5 gig because he upgraded? no idea once again
i have a mobo from on of the same ibooks so i think it is a ati mobility radon7500c

---

### Post by jacob01 on 2007-09-01
bump

---

### Post by stmiller on 2007-09-01
All hardware drivers are built in the Linux kernel, so you don't need to go fetch anything. Just boot this CD by holding down 'C':

[http://cdimage.ubuntu.com/ports/releases/feisty/release/ubuntu-7.04-desktop-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/feisty/release/ubuntu-7.04-desktop-powerpc.iso)

Let us know how it goes...

---

### Post by jacob01 on 2007-09-01
yea i made the disk and every thing an i am going to try it eithor on tuesday or wednesday whaen i go back to school and see the guy

---

### Post by jacob01 on 2007-09-04
bump

---

### Post by jerH on 2007-09-04
I have an old G3 iBook that I'm currently booting with a 7.04 live CD.  The machine has a bad hard drive, and a new one costs more than the computer is worth, so I'm experimenting.  The problem I'm encountering is that the display is all screwed up.  A vertical slice that's ~15-20% the width of the screen is black down the right side.  And the menu bar appears ~20% above the bottom of the screen.  If I move the mouse off the top of the screen the pointer reappears in the portion below the menu bar.  But windows don't wrap around, making it impossible to ever access the "continue" and "next" buttons at the bottom of any configuration screen.  There are only two screen resolutions listed as options in the screen preferences:  800x600 which gives the effect described, and 640x480 which is worse.  If you run into this, or figure out a way around it, let me know!

Thanks...

---

### Post by 3rdalbum on 2007-09-05
What sort of "black screen" is it?

If it's a completely black screen, then I've no idea.

If it's a black screen with a little picture of a crying Mac, then he should probably check that the RAM is good; he can test this by booting up Ubuntu or the Mac OS CD. If that works, then the system software is probably corrupted.

If it's a black screen with text on it, then booting into OS X's single-user mode might help - I believe you hold down "s" while starting up, although I can't confirm this.

---

