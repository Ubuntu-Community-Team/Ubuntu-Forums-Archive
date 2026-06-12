---
title: "Help with gdm setup, and greeter"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by drascus on 2007-04-12
I have been currently fooling around with the settings on gdmsetup such as changing the longon screen and sounds at logon. Somehow this has really messed up that program. when I start up it says the greeter program has crashed and it loads some sort of default. I have searched the forums and found no good answers. does anyone know how to solve this or how I might go about fixing this. 
Thanks
~Drascus~

---

### Post by justleen on 2007-04-12
logon to the default session which it loads, and start GDMSETUP again once logged on.

Change back to a default one.

Ive ran into the same, something it wrong with the theme which you have selected (in my case it was the img size i was trying to use).
Make a copy of a theme, rename it, and mess around in that copy!

---

### Post by drascus on 2007-04-12
ok I will try this and let you know what happens.

---

### Post by drascus on 2007-04-12
ok yeah it still says that the greeter program is crashing and then asks me to use another one. I don't get it. 
~Drascus~

---

### Post by justleen on 2007-04-12
did you select a default one? (one that you didnt mess with ;) )
try logging out, and restart GDM with CTRL-ALT-BKSPC

---

### Post by drascus on 2007-04-12
yes I tried the default human theme really had no effect but I am going to try the ctrl-alt-bkspace thing. 
~Drascus~

---

### Post by drascus on 2007-04-12
Ok I fixed it thanks. I apparently had the Enable accessible login tick box checked in the accessibility tab. I don't really know what that does but when I unchecked it it started working again. 
~Drascus~

---

