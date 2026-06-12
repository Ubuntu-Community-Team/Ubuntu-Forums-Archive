---
title: "A simple question about aesthetics"
date: 2009-03-19
forum: Apple Hardware Users
---

### Post by Rog-Mahal on 2009-03-19
This has nothing to do with hardware, and very little to do with Macbooks, so feel free to move this post, I just figured you guys might have the answer.

I really like the clean look of OS X, and I am trying to replicate some of my favorite aspects in Ubuntu. One thing has nagged me for a while now: I have yet to find a cursor theme that has a thin text entry...thing. I'm not sure what it's called, xterm perhaps? I really like how Mac did that one, it's only a pixel wide, which makes it really easy to place. 

Anyone know of such a theme? I have one that matches OS X in everything but that.

Thanks for the help, and my apologies if I posted this in the wrong place.

---

### Post by cyberdork33 on 2009-03-19
you mean that you want an I-Beam cursor for text entry instead of a block or underline? and are you talking about the mouse cursor?

In gnome terminal, there is an option to change what the cursor looks like in the preferences for the terminal cursor, but if you mean the mouse cursor, then you might just have to take a whack at modding what's there.

EDIT:
I had a look at the mac4lin cursor you are talking about (xterm) and it is ~3 pixels wide: a black line with a white border around it. The reason for this is that you need to be able to see it on a dark or light background. You might be able to get away with making a 2 pixel wide cursor that is just a black line with a white line next to it. This would ensure something could be seen with various backgrounds.

---

### Post by cyberdork33 on 2009-03-19
ok i modded the mac4lin cursor theme. This is about as thin as it gets. It was a bit harder than I thought it would be too.

---

### Post by Rog-Mahal on 2009-03-19
I was thinking of the I beam cursor, I think everything else looks fine. I think I was using a different theme than the one you mentioned, but I'll check that one out and see if I like it more.

---

### Post by cyberdork33 on 2009-03-19
> **Rog-Mahal said:**
> I was thinking of the I beam cursor, I think everything else looks fine. I think I was using a different theme than the one you mentioned, but I'll check that one out and see if I like it more.
Well it is not too hard to mod a theme as long as you have the images for the cursors you are using.

If you direct me to what you are using I can take a crack at it.

---

### Post by Rog-Mahal on 2009-03-19
Nevermind, your theme is perfect! Thanks a lot. Do you just use gimp to modify the images? That looks great! (Perhaps it's stupid to be excited about such a small thing, but thanks a lot.)

---

### Post by cyberdork33 on 2009-03-19
> **Rog-Mahal said:**
> Nevermind, your theme is perfect! Thanks a lot. Do you just use gimp to modify the images? That looks great! (Perhaps it's stupid to be excited about such a small thing, but thanks a lot.)yes, the mac4lin theme comes will with the source and images for the cursors, so I just modified the xterm cursor image (with gimp), rebuilt it, and tarred it back up. You could theoretically take the xterm cursor file and put it in another theme pack if that is what you want to do, but it sounded like to were trying to mimic OSX, and that was the best place I knew to get that.

---

### Post by Rog-Mahal on 2009-03-19
Cool, thanks a lot, next time I won't trouble you and do it myself. :)

---

