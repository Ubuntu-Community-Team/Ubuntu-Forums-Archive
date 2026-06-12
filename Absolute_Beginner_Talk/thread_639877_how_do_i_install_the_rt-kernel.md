---
title: "how do i install the rt-kernel?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by leader303 on 2007-12-13
hi everybody!
i have had issues with this in another thread, that has been forgotten, and maybe i did something wrong...
so: once again!
the question is: How do i install the realtime kernel on my gutsy? (preferrably in a way that not only grub and aptitude say it's installed, but i can actually boot and use it.)

---

### Post by leader303 on 2007-12-15
hmmm, nobody?
as said in [http://ubuntuforums.org/showthread.php?t=441366](http://ubuntuforums.org/showthread.php?t=441366) i installed linux-rt and as said in [http://ubuntuforums.org/showthread.php?t=599459](http://ubuntuforums.org/showthread.php?t=599459) i can't boot that thing.
what could have gone wrong? what info do you possibly need to help?

---

### Post by dcstar on 2007-12-15
> **leader303 said:**
> hmmm, nobody?
as said in [http://ubuntuforums.org/showthread.php?t=441366](http://ubuntuforums.org/showthread.php?t=441366) i installed linux-rt and as said in [http://ubuntuforums.org/showthread.php?t=599459](http://ubuntuforums.org/showthread.php?t=599459) i can't boot that thing.
what could have gone wrong? what info do you possibly need to help?

Boot off your old kernel, it should still be in your GRUB list.

PS, Don't put links in "HTML" code pairs, just leave them for the system.

---

### Post by leader303 on 2007-12-15
there's generic, lowlatency and rt with their respective recovery mode option. and i can boot the generic kernel (it's running right now as i am typing). but: i want to -use- the rt-kernel. what can i try?

---

### Post by leader303 on 2008-01-09
:confused:

seems like i have to ask again:
how do i install the rt-kernel right?

you know, that's what i'd like to know.

---

### Post by dcstar on 2008-01-09
> **leader303 said:**
> there's generic, lowlatency and rt with their respective recovery mode option. and i can boot the generic kernel (it's running right now as i am typing). but: i want to -use- the rt-kernel. what can i try?

You have a list in the menu, move the cursor to the one you want to use.

---

### Post by leader303 on 2008-01-10
i'm not talking about booting (because that thing won't boot). i assume i did something wrong in terms of installing (apt-get linux-rt, is that enough? i don't know! THAT is what i'm asking about).

---

### Post by kellemes on 2008-01-10
Well, I've never used the rt-kernel so I can only help you bughunt I guess..

Do I understand it correctly that you can select it from the bootmenu?
What's happening when you try to boot the rt-kernel?

---

### Post by sumguy231 on 2008-01-10
I think the linux-image-rt package is what you want. Out of curiosity, what do you need it for?

---

### Post by leader303 on 2008-01-10
kellemes: nothing really happens. black screen, flashing cursor.
sumguy: finally want to use ubuntustudio according to its intention: music production. with only generic kernel running, it's kinda pointless.
aptitude says, "linux-image-rt is already the newest version." so... what to do? uninstall? compile from source?

---

### Post by phil_bell on 2008-01-15
I sympathize leader303.  I can use generic kernels on my laptop, but not Ubuntu's pre-built realtime kernel.  In fact, I tried installing Ubuntu Studio and 64Studio on my laptop and neither will boot.  If I press and release the power button it will boot a little more then freeze.  I can do this several times, but it never boots all the way.  Once I tried removing the splash and quiet boot parameters, but I didn't  have the patience to go through the process several times and track what is freezing.

When I get a chance I'm going to try compiling a low-latency or realtime kernel using the generic kernel's config file as a template.  Also, maybe there is a way to post a message to the developer who builds linux-image-rt.  Just a thought.

---

