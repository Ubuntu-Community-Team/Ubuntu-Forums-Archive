---
title: "Help required, new ubuntu user"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by plwalter on 2008-01-23
Hi

I am a new user to ubuntu and have have installed 7.10 desktop on an old XP machine to test it out, it looks great.

However I noticed an alert about proprietory drivers for my NVida 8200 video card, so I (foolishly) clicked enable... after rebooting I now get a black screen with 'can't display this resolution' on my monitor (I think that's a message from my monitor, not ubuntu).

I found the 'recovery mode' on the grub menu, which takes me to a command line interface - I don't know what to do with it to disable this driver. Can I rollback changes?

Any help greatfully received.
Thanks
Peter

---

### Post by Kingfield on 2008-01-23
Type 

dpkg-reconfigure xserver-xorg (as root) :P

and follow the prompts, you should be able to do it (Nvidia driver by the way).

---

### Post by hyper_ch on 2008-01-23
actually it's:

```

sudo dpkg-reconfigure xserver-xorg

```

And change the thread title to something meaningful and don't just use a generic "noob here" or "need help"... you know, 99.99% of the threads here ask for help...

---

### Post by Kingfield on 2008-01-23
thats right. sorry about that :)

---

### Post by hyper_ch on 2008-01-23
> **Kingfield said:**
> thats right. sorry about that :)

well, you said "as root" but being new he may not know to use "sudo" to gain root privileges ;)

---

### Post by magump on 2008-01-23
I found the easiest way to install my Nvidia drivers is by using ENVY.  It configures everything for your card.  Download at: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

This works better for me than going to System>Administration>Restricted Drivers Manager.

---

