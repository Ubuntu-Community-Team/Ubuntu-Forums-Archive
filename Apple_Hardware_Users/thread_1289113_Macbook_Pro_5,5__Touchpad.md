---
title: "Macbook Pro 5,5  Touchpad"
date: 2009-10-12
forum: Apple Hardware Users
---

### Post by N_Nick on 2009-10-12
I just installed Karmic on the new 5.5 13" Macbook Pro and there's one thing I cant figure out how to do it.

As you know on the new Macbooks the click button is part of the touchpad itself.

On the previous Macbooks (and on this in OSX) I was used to having my thumb on the click button and moving the cursor around with my pointer. Under OSX that still works but Ubuntu registers that as right click so I cant move the cursor.

Is there a way to get it to ignore the second finger on the touchpad, so i am able to move the cursor?

Thanks

---

### Post by ALLurGroceries on 2009-10-12
> **N_Nick said:**
> I just installed Karmic on the new 5.5 13" Macbook Pro and there's one thing I cant figure out how to do it.

As you know on the new Macbooks the click button is part of the touchpad itself.

On the previous Macbooks (and on this in OSX) I was used to having my thumb on the click button and moving the cursor around with my pointer. Under OSX that still works but Ubuntu registers that as right click so I cant move the cursor.

Is there a way to get it to ignore the second finger on the touchpad, so i am able to move the cursor?

Thanks

You can try the method I've outlined here:
[http://forum.notebookreview.com/showthread.php?t=418403#touchpad]("http://forum.notebookreview.com/showthread.php?t=418403#touchpad")

Good luck :)

---

### Post by N_Nick on 2009-10-13
> **ALLurGroceries said:**
> You can try the method I've outlined here:
[http://forum.notebookreview.com/showthread.php?t=418403#touchpad]("http://forum.notebookreview.com/showthread.php?t=418403#touchpad")

Good luck :)

Unfortunately that didn't work.

Your sound instructions were really helpful though, i finally got my macbook pro to talk :)

---

### Post by ALLurGroceries on 2009-10-13
> **N_Nick said:**
> Unfortunately that didn't work.

Your sound instructions were really helpful though, i finally got my macbook pro to talk :)

Hm sorry about that. Must be different for Karmic, I run Debian Sid. It's not a *real* fix anyway. It works well for me for click and drag, otherwise I was stuck with the two finger right click only.

---

### Post by proycon on 2009-10-17
I'm having the same problem on a Macbook Pro 5,3. It seems the hal settings aren't used at all, 'synclient -l'  reports very different settings as the ones I attempted to set in the FDI file.

---

### Post by proycon on 2009-10-17
Not a very elegant solution, but you can call synclient to set the desired properties. 

I wrote a little script, aiming to at least get click and drag working. I did so by disabling movement on the bottom portion of the mousepad, mimicking a traditional setup. Unfortunately this conflicts with two-finger scrolling, so I had to disable that and use right-edge scrolling instead.

If someone can find better settings, please post them.

---

### Post by N_Nick on 2009-10-18
> **proycon said:**
> Not a very elegant solution, but you can call synclient to set the desired properties. 

I wrote a little script, aiming to at least get click and drag working. I did so by disabling movement on the bottom portion of the mousepad, mimicking a traditional setup. Unfortunately this conflicts with two-finger scrolling, so I had to disable that and use right-edge scrolling instead.

If someone can find better settings, please post them.

I will check it out in a bit and get back to you. Does two finger scrolling work on the top part of the touchpad?

---

### Post by proycon on 2009-10-21
> 
Does two finger scrolling work on the top part of the touchpad? 


No, unfortunately that option seems not to take my area restrictions into account (not sure if this is intentional or a synaptics bug).


However, I made an alternative setup now, which I personally find better and quite workable. But it's also a matter of taste.

My previous setup did not have double-finger scrolling, due to it conflicting with click & drag. This new setup does have double-finger scrolling, but that means that click & drag no longer works. Instead, I enabled all forms of tapping, and the actual button can only be used for left-clicking without drag. Dragging is initiated double-tap. A right click by a tap with two fingers, and a middle click a tap with three fingers (useful for pasting!).

I've attached the revised script. There's probably a more elegant solution than running this script at startup time, but this works.

---

