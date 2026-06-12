---
title: "Desktop icons flash on and off"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Delirious on 2007-07-11
Somehow my desktop icons that were present and any new ones i add are hidden. They are there but only show up when i move my cursor over them. 

The only thing i can think of that would maybe affect this would this change i made to xorg to fix the flickering with conky. Now my conky doesnt flicker but my icons do? 

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
	Load 		"dbe"
EndSection

---

### Post by Delirious on 2007-07-11
No one have any ideas?

---

### Post by der_joachim on 2007-07-13
I have the same problem. Although so far i haven't been able to solve it, maybe I can help you a bit.

Apparently, the disappearing icons have something to do with the dbe module. Disabling it in your xorg.conf will solve our mutual problem. However, some programs (like conky) will not work properly without it.

Since I use conky, disabling dbe is not an option for me.

---

### Post by maltman on 2007-10-04
I know this is an older thread, but I am having the same issue as well.
Does anybody have a solution for enabling "dbe" in xorg.conf so conky doesn't flicker, but also so desktop icons don't disappear?
Thanks!

---

### Post by maltman on 2007-10-05
Ok, I found the answer elsewhere on this forum.

So after I set "double_buffer yes" in my .conkyrc, and added   Load "dbe" to my xorg.conf, what I also needed to add was the following to my .conkyrc and all is fine. No flickering conky, and all desktop icons are as they were.

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

---

