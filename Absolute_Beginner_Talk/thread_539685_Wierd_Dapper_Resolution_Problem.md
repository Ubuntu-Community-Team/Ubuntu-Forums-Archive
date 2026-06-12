---
title: "Wierd Dapper Resolution Problem"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Simpleton on 2007-08-31
I've done many things with the xorg but still have this really wierd problem.

When I select 1680x1050 the computer displays at 1400x1050 (but fills the screen)

However when I select 1400x1050, the computer displays at 1680x1050, but the desktop is squished into a 4:3 size on the far right of the widescreen. But when you click the OSD on the monitor it confirms it is in 1680x1050

I am running an ATI x800 PRO, with an lg 22 inch widescreen (that is fine on my XP boot).

Any help would be appreciated, cos the blurry text is hurting my eyes.

PS on both selections the refresh is 60Hz as selcted!

Wierd eh?!?!

---

### Post by GMachine_24 on 2007-09-01
Well, X11 is ..or can be......problematic. Very.

So............post your X11 file here and let everyone have a look at it.

Have you checked the X11 man pages?

If you happen to have a copy of the latest FreeBSD book from Sam's publishing it gives a lot of great information about setting up and trouble shooting the X11 file and video................I know... a shot in the dark....

Do you have the horiz and vert sync rates for your monitor?

etc

--gm

---

### Post by Simpleton on 2007-09-02
Thanks for the reply.

I have sort of sorted it!

I added fglrx, which is ok, expect I can't get the log in screen to work and it doesn't shut down properly.

Still once Vista arrives through the post, I'm gonna reformat and create dual boot with Vista and Fiesty.

Have downloaded the ATI - X**** routines for installing the new one.

Comedy really, built the computer before I discovered Linux, but I had already bought the ATI card thinking there would be little difference between nVidia and ATI. If only I knew then what I know now!

haha:lolflag:

---

