---
title: "Weird problem on newer Edgy kernel"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2007-02-13
I updated to Edgy yesterday and everything went well. Then I decided to install Beryl before finding out it wasn't compatible with my graphics card, so I uninstalled it. This morining I turned on my laptop and booted into the newer Edgy kernel 2.6.17.11-386(?) and programs will not always open up, and I cannot get my wireless internet working. However everything on my older kernel (2.6.15-28-386) works fine (I am posting this message while booted into this kernel!)

Also, when I did get Terminal to open up on the new edgy kernel, the command line looked like this:

```
matt@(none):~$
```

Whereas the command line looks like this on the older kernel:

```
matt@:~$
```

Does anyone know what could have caused the 2.6.17.11-386 system to mess up? I must stress that everything worked fine before uninstalling Beryl late last night.

Cheers

---

### Post by Tmi on 2007-02-13
I'm not an expert on this, but it sounds like you are having the same problem with your wireless as I had with my graphics card after the kernel update. The fix for this is to install the drivers for your nonworking card over again in the new kernel also since they arent included when the kernel updates (they are still installed on the previous kernel and thus everything works there). At least for my graphics card I could install them from the previous and working kernel with a speciall command, and after booting the new kernel it all worked. How to do this for a wireless card I don't know, but somebody else can probably help you with that.

---

### Post by spamzilla on 2007-02-13
That may be the case, however I could connect to the internet fine on the new kernel last night. Everything else worked fine last night too :/

---

### Post by sunexplodes on 2007-02-13
well, that's weird. 

this is a shot in the dark, but in the terminal when it says matt@(none): the "none" part should be your hostname. So open up System>Administration>Network, go into the "General" tab and add a hostname. Doesn't matter much what it is, it's just a name for your computer to be identified by on the network. 

Once you change it, log off and then back on. I have no idea if it will solve your problem, but it may be worth a shot.

---

### Post by spamzilla on 2007-02-13
That fixed my problem and all programs now seem to be working fine!

Thanks a lot :)

---

### Post by sunexplodes on 2007-02-13
Wow, I'm actually a little surprised, but I'm glad it worked.

---

