---
title: "Which linux-image for me?"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by wog on 2006-06-11
I'm trying to ask just one question at a time so I don't get confused.

In Synaptic, I see I'm using linux-image-386, but I'm also using linux-image-2.6.15.23-386. Can I be using both at the same time, or are they just different names for the same thing?

---

### Post by mcduck on 2006-06-11
[QUOTE=wog]I'm trying to ask just one question at a time so I don't get confused.

In Synaptic, I see I'm using linux-image-386, but I'm also using linux-image-2.6.15.23-386. Can I be using both at the same time, or are they just different names for the same thing?[/QUOTE]
The linux-image-2.6.15.23-38 is the actual package. linux-image-386 is a metapackage that always depends on the lates linux-image-386 version available. So as long as you have it installed, when new version becomaes available the update-manager will offer it for you.

If you take a look in Synaptic, you'll also find another metapackage, linux-386. Yhis one depends on latest version of the linux kernel image, kernel headers and restricted modules. Having this one installed that you always have latest versions of all those..

There's also linux-686 (for pentiums and later Intel & AMD CPU's) and linux-K7 (for Athlons and later AMD CPU's). If you have one of those processors, you might want to install linux-386 or linux-K7 and use it instead of linux-386 :)

---

### Post by wog on 2006-06-11
Okay, so that answered a question I hadn't got to yet.

So to change to k7, do I install linux-image-k7 and let it decide what else to install, or do I need to specifically the latest k7 kernal to add as well?

---

### Post by mcduck on 2006-06-11
[QUOTE=wog]Okay, so that answered a question I hadn't got to yet.

So to change to k7, do I install linux-image-k7 and let it decide what else to install, or do I need to specifically the latest k7 kernal to add as well?[/QUOTE]
neither one. Install the linux-K7 package, and you'll get everything you need, and also updates for your new K7 kernel.

---

### Post by wog on 2006-06-11
Okay, next associated problem.

Since the nVidia drivers are bound up in the kernal, does this mean every time there's a new kernal I'll have to reinstall the nVidia driver?

---

### Post by mcduck on 2006-06-12
[QUOTE=wog]Okay, next associated problem.

Since the nVidia drivers are bound up in the kernal, does this mean every time there's a new kernal I'll have to reinstall the nVidia driver?[/QUOTE]
I know nothing about nVidia driver, but at least with my ATI drivers (installed from Ubuntu repositories) everything works fine as long as I make sure that when I update my kernel I also get restricted modules for the new kernel version. I'd think it's the same with nVidia drivers from repositories.

---

### Post by wog on 2006-06-13
Hm. I wonder if it's the same?

Do ATI drivers insert themselves into the kernal?

---

### Post by tseliot on 2006-06-13
[QUOTE=wog]Okay, next associated problem.

Since the nVidia drivers are bound up in the kernal, does this mean every time there's a new kernal I'll have to reinstall the nVidia driver?[/QUOTE]
The answer is yes.

If you used the driver in the repos you only need to install the restricted modules for your new kernel.

If you used the Nvidia installer from Nvidia's website you need to install the kernel headers for your new kernel and run the installer again.

---

### Post by wog on 2006-06-13
[QUOTE=tseliot]
If you used the driver in the repos you only need to install the restricted modules for your new kernel.

If you used the Nvidia installer from Nvidia's website you need to install the kernel headers for your new kernel and run the installer again.[/QUOTE]

It's sounding so far like installing the restricted modules from the repositories is easier, but I can't tell yet.

So if I install the restricted modules (I'm assuming that means linux-restricted-modules-k7 if I have the k7 kernal installed), I basically don't have to worry about reinstalling the new nvidia drivers as they come out because they'll be included in the updates from then on. In fact, I'm not sure why anyone would go the route of installing the kernal headers unless they were in the development team. Is that about right or am I confused again?

---

### Post by brentoboy on 2006-06-13
wog,
your system sounds just like mine
get linux-k7
get nvidia-glx
make sure you also have the restricted modules to match your kernel.

EDIT: if you use these (instead of compiling the drivers from the nvidia site, it will keep them up to date for you--no worries)


once you reboot, use grub to select the k7 kernel

if it works great, use synaptic to remove the other (386) kernel stuffs.

---

### Post by brentoboy on 2006-06-13
[QUOTE=wog]I'm not sure why anyone would go the route of installing the kernal headers unless they were in the development team. Is that about right or am I confused again?[/QUOTE]

if you had an nvidia card that was so new that it wasnt supported by the version being used by ubuntu, then you would get the driver from the nvidia site and do all that extra compiling etc.

other than that, there isnt much reason to do it.

ubuntu doesnt always have the latest drivers, it has the driver build from when development started on the particular version of ubuntu.  so, dapper's nvidia drivers are the ones from late 2005.  when nvidia releases new ones, they are not inculded until the next release of ubuntu (its a testing/stability thing).

---

### Post by wog on 2006-06-13
[QUOTE=brentoboy]wog,
your system sounds just like mine
get linux-k7
get nvidia-glx
make sure you also have the restricted modules to match your kernel.

EDIT: if you use these (instead of compiling the drivers from the nvidia site, it will keep them up to date for you--no worries)


once you reboot, use grub to select the k7 kernel

if it works great, use synaptic to remove the other (386) kernel stuffs.[/QUOTE]

Okay, so I get linux-k7, reboot, then linux-restricted-models-k7, then reboot again and then nvidia-glx and reboot one last time?

When I had Breezy I installed the k7 kernal and the nvidia-glx thingie and didn't reboot at all. Given that when I finally did reboot my gdm went down for the count I know I'm supposed to reboot at least once in there to make sure it's all working before putting something else in there.

---

### Post by brentoboy on 2006-06-14
no -- get them all at once.
dont remove any old kernels and their associated modules until you have it all working on the k7 one.

after you have all three packages installed, reboot.

when grub asks you what kernel to boot from choose the k7 one.

when x-windows starts up, the nvidia logo screen should flash up for a second or two -- if that happens, you are in business.

then you can remove old kernels, there is only need to reboot once.  You never "have" to reboot except when replaceing a kernel, updating the video driver just requires you to restart xwindows.

for future reference, if you only want restart X then you can do this...

ctrl+alt+f1
will bring you to a text console.

sudo /etc/init.d/gdm restart
will restart xwindows without rebooting

---

### Post by wog on 2006-06-14
Odd. When I installed linux-k7 a large number of things were installed all at once, and nvidia-glx must've been one of them since the splash screen for nvidia came right up. I certainly noticed one of the things automagically installed was linux-restricted-modules-k7.

Thank you, everyone. I think this issue is solved. :)

---

### Post by az on 2006-06-14
[QUOTE=wog]I certainly noticed one of the things automagically installed was linux-restricted-modules-k7.
[/QUOTE]
Yes, it is a dependancy of linux-k7.

Stop reading here if you don't want to get confused.

linux-k7 depends on linux-image-k7 and linux-restricted-modules-k7.  Let's say that I want to get rid of the restricted modules on my system because I don't want to use proprietary drivers.  I get rid of linux-restricted-modules-2.6.15-k7 and that takes the linux-restricted-modules-k7 and linux-k7 metapackages along with it.

But it leaves linux-image-k7 behind.

So I still can have a functioning system that gets the latst packages because my linux-image-k7 metapackage is still there.

That's why there are so many different kernel metapackages.

---

### Post by wog on 2006-06-15
I can't help reading. As long as you keep typing I'll keep trying to understand you, although I think I got all that. I don't think I would be ready for such specific choices as you mention in your example, tho. I still have to get used to the structure of Linux. :)

I'll get it eventually, though. I just have to keep after it.

---

