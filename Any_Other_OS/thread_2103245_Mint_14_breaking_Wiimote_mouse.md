---
title: "Mint 14 breaking Wiimote mouse?"
date: 2013-01-09
forum: Any Other OS
---

### Post by Rebelli0us on 2013-01-09
Registering in the Mint forums seems impossible, so I’m posting here instead.

I have several installations of Mint 14 where the Wii remote mouse-pointer malfunctions, whereas it works fine in Mint 13 on the same machine.

You click a button in some location on the screen and a button in a different location gets pressed. The mouse-cursor jumps around erratically, mostly to the top-left position on the screen (so in a maximized app it opens the System menu, instead of the location you’re clicking). I’m also getting intermittently TWO mouse cursors.

The Wiimote driver works OK but it seems there is a problem with the OS’s mouse driver (or whatever is responsible for cursor movement).

Can anybody confirm this behavior?

---

### Post by xenopeek on 2013-01-09
I've sent you a private message about the problem you had with registering on the Linux Mint forum. I'd be happy to help you solve it.

As for your problem, are you using the same desktop environment on Linux Mint 13 and 14? That might be a factor.  I think you will have set up the Wiimote similar as from [this guide]("https://help.ubuntu.com/community/CWiiD")?

---

### Post by Rebelli0us on 2013-01-09
> **xenopeek said:**
> I've sent you a private message about the problem you had with registering on the Linux Mint forum. I'd be happy to help you solve it.

As for your problem, are you using the same desktop environment on Linux Mint 13 and 14? That might be a factor.  I think you will have set up the Wiimote similar as from [this guide]("https://help.ubuntu.com/community/CWiiD")?


Thank you. Yes I’m using Mint MATE in both 13 and 14, and Wiimote is installed correctly. The problem is very consistent on both AMD and Intel platforms: 13 works fine, in 14 the pointer jumps around.

---

### Post by xenopeek on 2013-01-10
I check the versions of the packages the linked guide would have you install on Maya and Nadia. The versions of these packages don't differ between these releases, so that can not be the cause (all are version 0.6.00+svn201-3build1). The guide has you load the kernel module uinput, for mouse emulation, which is included in the Linux kernel. The kernel does differ: 3.2.0-23 for Maya, 3.5.0-17 for Nadia. This may be some problem with in the kernel version you are using?

That module doesn't seem to have been changed recently, but it include a lot of other files so one of those may have changed: [http://lxr.linux.no/#linux+v3.5/drivers/input/misc/uinput.c](http://lxr.linux.no/#linux+v3.5/drivers/input/misc/uinput.c).

You may try using a newer kernel perhaps? Check your current kernel version with:
```
uname -r
```
If it is still 3.5.0-17-generic, go to Update Manager. Open Edit > Preferences and enable level 4 and 5 upgrades. This will upgrade your kernel to 3.5.0-21-generic.

You can also jump up to another 3.5.x kernel series, or a 3.6.x kernel series. That's explained here: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds). I'd stick to installing quantal kernels on Linux Mint 14 BTW.

---

### Post by Rebelli0us on 2013-01-10
> **xenopeek said:**
> I check the versions of the packages the linked guide would have you install on Maya and Nadia. The versions of these packages don't differ between these releases, so that can not be the cause (all are version 0.6.00+svn201-3build1). The guide has you load the kernel module uinput, for mouse emulation, which is included in the Linux kernel. The kernel does differ: 3.2.0-23 for Maya, 3.5.0-17 for Nadia. This may be some problem with in the kernel version you are using?

That module doesn't seem to have been changed recently, but it include a lot of other files so one of those may have changed: [http://lxr.linux.no/#linux+v3.5/drivers/input/misc/uinput.c](http://lxr.linux.no/#linux+v3.5/drivers/input/misc/uinput.c).

You may try using a newer kernel perhaps? Check your current kernel version with:
```
uname -r
```
If it is still 3.5.0-17-generic, go to Update Manager. Open Edit > Preferences and enable level 4 and 5 upgrades. This will upgrade your kernel to 3.5.0-21-generic.

You can also jump up to another 3.5.x kernel series, or a 3.6.x kernel series. That's explained here: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds). I'd stick to installing quantal kernels on Linux Mint 14 BTW.

I am tickled to see the code for uinput because I’m a big fan of the Wiimote, too bad Nintendo has discontinued that model.

Thank you, yes Mint 14 is stock 3.5.0-17-generic. Why don’t I simply update just the kernel, instead of allowing “unsafe” and “dangerous” packages? I had to do that in Mint 13 because it does NOT support the Intel z77 platform, so I’ve upgraded the kernel to 3.5-something. In 13 I’ve also enabled “backported packages”, no other changes, and it works **very** well, including the Wii.

My Mint 14 is stock version, works fine with NO changes, except for the Wiimote problem I’ve described.  

I also have a portable Mint in a USB flash drive, it’s very “universal” so it will boot on any machine regardless of video hardware, etc.  I take it with me when I’m in Europe and use it to give presentations using Wii as mouse pointer. I have all versions of Windows yet I choose Mint for my work, so that says a lot.

And I thank you for the link to MainlineBuilds. Honestly, even as a sometime Windows developer these instructions are meaningless to me. I’d much rather let the Update Manager do it. But I will update the Mint 14 kernel somehow and report back if it fixes the Wii problem.

---

### Post by Rebelli0us on 2013-01-24
As promised, this morning I installed kernel 3.7.1 but the OS self-destructed. I'm down to 640x480 and NVIDIA is not loading. Any ideas?


```
     cd /tmp 

    wget http://dl.dropbox.com/u/47950494/upubuntu.com/linux-kernel-3.7.1 -O linux-kernel-3.7.1 

    chmod +x linux-kernel-3.7.1 

    sudo sh linux-kernel-3.7.1 


```

---

### Post by Rebelli0us on 2013-01-25
I switched to kernel 3.6.9, the video works but the bug is still there. To reproduce the problem:

- With Wii remote, press & hold the left mouse button, and do circles around the screen.
- As you approach the top left area, the selection rectangle will start jumping around.
- Also when the mouse pointer is near the top-left corner you’ll see two mouse pointers.

This bug does NOT exist in Mint 13, and I hope it doesn’t propagate to future versions of Mint.

---

