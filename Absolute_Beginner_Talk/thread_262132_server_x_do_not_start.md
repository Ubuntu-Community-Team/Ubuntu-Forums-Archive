---
title: "server x do not start"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by jawa00 on 2006-09-21
Dourig boot phase video shows a blue screen and in the center a message which says "can't start the server X", see  more details ...yes or no....
I choose option <no> than comes a text page for log in.

I logged in with my UD and Passw than I type manually <startx>  now the x server start properly so I can play with my linuxbox untill nex reboot where problem comes again.

pls. can anyone help me? :confused:

---

### Post by Metacarpal on 2006-09-21
I'm gonna go out on a limb here and guess that you have an nvidia or ATI graphics card and just downloaded a kernel update, right?

If so, remember having to install the driver for your video?  You'll have to do it again, as the driver install is dependant upon the kernel - so when the kernel changes, your driver goes poof.

I don't have that type of card, so I can't help with reinstalling the driver - but I can help with getting you back on your computer for the time being to do the fix.

When you first start your computer and the GRUB menu is loading, hit Esc on your keyboard.  This will show a list of kernel versions.  Select the *second-highest* version.  That should get you up and running, and from there you can fix the driver issue.

If you're not sure how, do a quick search of the forum - there are lots of helpful threads already out there.

Best of luck!

---

### Post by mcduck on 2006-09-21
> **Metacarpal said:**
> I'm gonna go out on a limb here and guess that you have an nvidia or ATI graphics card and just downloaded a kernel update, right?

If so, remember having to install the driver for your video?  You'll have to do it again, as the driver install is dependant upon the kernel - so when the kernel changes, your driver goes poof.

I don't have that type of card, so I can't help with reinstalling the driver - but I can help with getting you back on your computer for the time being to do the fix.
This is not true. As long as you install the graphics card drivers from ubuntu repositories, and have linux-386, linux-686 or linux-k7 (or whatever version fits you kernel) metapackage installed you don't have to reinstall graphics card drivers again. This pacakge makes sure that you always have latest versions of all kernel-related files. Without it you might get an update for your kernel but not for restricted modules, and that would cause your graphics card drivers to fail working..

If you compiled your own kernel, or if you installed the drivers from Ati/nVidia website, the it's of course a different case.

---

### Post by Metacarpal on 2006-09-21
Oh.  I stand corrected, then - I just thought I'd just seen a lot of threads where people with proprietary nvidia drivers lost X after a kernel update.

---

