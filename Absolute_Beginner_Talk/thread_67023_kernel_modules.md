---
title: "kernel modules"
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by myha on 2005-09-19
Hi!

Does someone maybe know where I could find list of modules and stuff explained for kernel? I would like to see explained what does diffrent module do....

And can also smbdy explain me the diffrence between Module and * when u compile kernel?

thanks,
miha

---

### Post by macgyver2 on 2005-09-19
[QUOTE=myha]Hi!

Does someone maybe know where I could find list of modules and stuff explained for kernel? I would like to see explained what does diffrent module do....

And can also smbdy explain me the diffrence between Module and * when u compile kernel?[/QUOTE]
Hi myha...

Regarding your second question, when you use kernel modules you are, well, modularizing your kernel.  For instance, say some developers want to have a general kernel that works with as many different computers as possible (as most distro developers do).  There are dozens of drivers in the kernel for network cards alone.  It doesn't make sense to have all of them compiled into the kernel because you usually only need one or maybe two of them for a particular machine.  So the developers make all of the different drivers modules.  Computer A might require the 8139too driver, so module driver is loaded and the rest are not.  Computer B might require the tulip driver, *not* the 8139too driver...so the the tulip module is loaded and the rest are not.  Of course, when you get into *all* the possible devices that have drivers in the kernel, if you compiled  *everything* in you'd end up with quite a massive, bloated kernel.

Even if you're making a kernel for a specific computer modules can come in handy.  If you only use a certain device occasionally (a decent example I can think of right now is an external usb harddrive) you only need those drivers in the kernel occasionally.  If you compile those drivers into the kernel then they're there, loaded, all the time, and that bloats your kernel,  If you compile those drivers as modules, then the modules can be loaded when the device is plugged in and unloaded with the device is unplugged.  Nowadays that all happens automatically, for the most part.

So in summary...by using modules, you can get a streamlined kernel that doesn't have a lot of unused stuff in it but at the same time you can still have the other stuff available if you need it, without having to go back and recompile it into the kernel.

Now, as for a list of modules that includes explanations...[this module howto]("http://www.tldp.org/HOWTO/Module-HOWTO/") has some.  Otherwise, you can look while you're configuring the source...most kernel options come with a short explanation of what that option does.  There might be other places but I just don't know of them.

If you're interested in knowing more about the kernel there's a really good site  for those just starting to learn [here]("http://kernelnewbies.org/") (and of course more information about modules in that howto I linked to above).

Hope that helps!

---

### Post by myha on 2005-09-20
Hi!

First of all thank you for your extensive answer... I think I understand a bit more now... I'll have a look at the how-to you posted to know more when I have time...

Thank you very much,

regards,
Miha

---

