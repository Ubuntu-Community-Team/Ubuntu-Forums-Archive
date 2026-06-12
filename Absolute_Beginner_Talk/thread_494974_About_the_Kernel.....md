---
title: "About the Kernel...."
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by ElEdwards on 2007-07-07
As I dive deeper in the world of Linux (using Ubuntu 7.04), I see articles and postings regarding "a new kernel" and "kernel patches", etc....
....so I have some questions (since I haven't yet located a HOWTO on this):

- Would there be any advantage(s) to me learning how to update my kernel?

- What are the pitfalls?

- What are the chances that I'll break my Ubuntu?

Thanks :)

El

---

### Post by Zzl1xndd on 2007-07-07
Kernel Updates come down the line in Ubuntu via the update Manager, its normally not right a way but you will get them :)

---

### Post by Rui Pais on 2007-07-07
> **ElEdwards said:**
> As I dive deeper in the world of Linux (using Ubuntu 7.04), I see articles and postings regarding "a new kernel" and "kernel patches", etc....
....so I have some questions (since I haven't yet located a HOWTO on this):

[biblic voice] The [master thread]("http://ubuntuforums.org/showthread.php?t=311158") will tell you all ... [/biblic voice]
> 
- Would there be any advantage(s) to me learning how to update my kernel?

You may learn a little about kernel internals, compile/patch, modules and how they work. You can tune it for your hardware, and try new stuff. You will, too, became awesome at the eyes of the opposite sex, but thats a secondary effect and will disappear in a few hours. 
Seriously. Ubuntu kernels had too much things enabled by default (debugging stuff... and support for things that one usually don't have, compiled inside, etc...) And i found weird behavior that i don't have in some more wild, experimental patchs. Try for instance the suspend2 patch, it work so wonderful and fast... and then count then countless threads about suspend is broken in Ubuntu...  
> 
- What are the pitfalls?

Large things with crocodiles inside. Crocodiles are nice and not too hot in the summer.
Ok. Most of the time is an exercise on futility... in practical terms. :) 
If everything works now, maybe it shouldn't deserve the try... In my case, i never been much lucky with ubuntu kernels and i liked my one ones :) (right now i use 2.6.21-viper2)
> 
- What are the chances that I'll break my Ubuntu?

Kernels are installed side by side in your /boot. If the one you make is broken just reboot with the Ubuntu kernel. Don't use patchs for experimental filesystems, they can corrupt/lost data.

> 
Thanks :)

El

I hope i had obscure a little more your question :p

---

### Post by ElEdwards on 2007-07-07
Excellent info :)  Thanks!

I think that for now, I'll wait until being awesome in the eyes of the opposite sex lasts linger ;)

---

