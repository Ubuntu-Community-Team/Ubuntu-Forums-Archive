---
title: "new machine and ubuntu"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by asi594 on 2007-10-08
Hi

I'm about to get a new system.  Does ubuntu make use of multiple cores "out of the box" or is there a config necessary?

any other help on where to look for advise on building a brand new machine and making sure it'll be good friends with ubunutu and linux in geneneral?

thanks

---

### Post by hyper_ch on 2007-10-08
well, the troublesome hardware is normally:

- video card
- wifi
- bluetooth
- sound

Check the Ubuntu Hardware in the wiki to see what is good supported.

---

### Post by cameronw on 2007-10-08
To enable multiple cores you need to install the SMP (Symmetrical Multi-Processor) kernel. Search for linux-image in Synaptic and install the 686-SMP kernel. Then when you boot up you can select the newly installed kernel and you will make use of multiple cores.

---

### Post by asi594 on 2007-10-08
thanks, looks easy enough. 
and the hardware list looks useful.

---

### Post by cameronw on 2007-10-08
By the way if you want to change it to start the SMP kernel by default edit your /boot/grub/menu.lst and find the SMP kernel in the list near the bottom. Move the one you want to default to the top of that list. Next time you boot it should load without having to select it.

---

### Post by hyper_ch on 2007-10-08
cameronw:

Actually that's not the way how you should define what kernel is booted by default...

You should use the
```

default         0

```

option instead. Once you verified that multi-core kernel works fine, then you just remove the single-core ones...

---

### Post by cameronw on 2007-10-08
Oh I was sure that was the way you do it but thanks for that. I like to keep my original kernel anyway just in case of any problems that might arise.

---

### Post by hyper_ch on 2007-10-08
cameronw:

Well, you can have multiple kernels installed... I always keep the newest one plus the one before... so if there are issues with the newest one I can fallback to the old one :)

---

