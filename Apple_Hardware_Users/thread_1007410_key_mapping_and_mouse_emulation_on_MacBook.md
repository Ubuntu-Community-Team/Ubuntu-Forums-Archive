---
title: "key mapping and mouse emulation on MacBook"
date: 2008-12-10
forum: Apple Hardware Users
---

### Post by beauman on 2008-12-10
I did revise the keyboard section of


[https://wiki.ubuntu.com/MacBook/SantaRosa]("https://wiki.ubuntu.com/MacBook/SantaRosa")

a bit, so that:
[LIST]
[*] The CapsLock LED will work
[*] right click = right alt
[*] middle click = left cmd
[*] altgr = right cmd
[/LIST]

any feedback welcome

---

### Post by beauman on 2008-12-11
I have changed the mapping in the wiki, so the usage is more
intuitive:

[LIST]
[*] middle click= left cmd
[*] right click=right cmd
[*] everything else default
[/LIST]

Now my keyboard support is really perfect, except one tiny little thing:
If I press **CD eject**, the CD eject symbol won't appear on the 
display. I can map a different key to work as the eject key, like for
example F6, and the eject symbol will be shown when using it. But 
the eject key is not recognized in the keyboard mapping dialog. I think,
it only works with pommed.

---

### Post by cyberdork33 on 2008-12-11
> **beauman said:**
> But 
the eject key is not recognized in the keyboard mapping dialog. I think,
it only works with pommed.
I believe there is a kernel bug and this is why the key is not recognized (without pommed). Probably need a bug report.

---

### Post by beauman on 2008-12-11
Yes, it's funny. I remember, that it used to work.

Cyberdork, there is an other thing, that came up today. From the posts at launchpad and from my own experiences, I had figured, that removing  mouseemu will fix the bug with the caps lock LED. Can you imagine that this is only true for the MB 4,1, but not for MBP 4,1 (see ["Macbook caps lock light"]("http://ubuntuforums.org/showthread.php?t=1002463"))

Also, do you think it is possible to get the exact mouse and keyboard behavior as under OS X?

---

### Post by cyberdork33 on 2008-12-12
> **beauman said:**
> Yes, it's funny. I remember, that it used to work.

Cyberdork, there is an other thing, that came up today. From the posts at launchpad and from my own experiences, I had figured, that removing  mouseemu will fix the bug with the caps lock LED. Can you imagine that this is only true for the MB 4,1, but not for MBP 4,1 (see ["Macbook caps lock light"]("http://ubuntuforums.org/showthread.php?t=1002463"))

Also, do you think it is possible to get the exact mouse and keyboard behavior as under OS X?
mouseemu is not required for any Intel Mac. It has been plaguing us since I can remember. IDK if it fixes the Caps Lock light for others though.

What is "exact mouse and keyboard behavior"?

---

### Post by beauman on 2008-12-12
> **cyberdork33 said:**
> 

What is "exact mouse and keyboard behavior"?

I ment "Do you think, it is possible to get exactly the same mouse and keyboard behavior under Ubuntu as under OS X?". What I had in mind is for example ctrl+click. I am still thinking about the solution I proposed with right/middle emulation on the two cmd keys. It works pretty good, but it still feels a bit self-made. I am not familiar with all input gestures you can make under OS X, but I bet they are quite elaborate.

Anyway, I also found out (with the help of regebro) how to configure the two-finger-tap for right click emulation. This is actually the perfect way to get it. Very good to handle. But that's (for the MB) just for version 3.1 or bigger, correct me if I'm wrong. 

The question is also, what we actually can do about mouseemu. The bug is filed on launchpad, and will hopefully be fixed quite soon. But it's still annoying that the default mouse click emulation is Fn+F11/F12 (which also  disables the fullscreen hotkey for a lot of applications). Does the kernel really know, that it's a Mac keyboard? And would it then be possible to start mouseemu with a dedicated configuration file?

---

