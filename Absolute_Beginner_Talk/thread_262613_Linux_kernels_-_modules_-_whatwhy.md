---
title: "Linux kernels - modules - what/why?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by madcow72 on 2006-09-21
I'm obviously fairly new to the Linux community. (Obvious because that's the name of this forum.)  I have a couple general questions and probably one more specific.

1)  What exactly is the kernel?

2)  I've found some howto's in my searches on other topics which mention having to download the kernel-source and compile it.  Is this something everyone needs to do?

3)  I've noticed that recently there was a kernel update from Adept - why does one need to update the kernel?

4)  The reason I ask this last question in particular is what leads me to my specific question:  Yesterday I rebooted my computer and noticed that GRUB gave me a new choice of kernels to boot from, the new one and the old.  If I choose the new one the computer freezes when trying to enter X - I get a black screen and Alt+F2, CTRL-Alt-Backspace don't do anything.  If I choose the old kernel, everything works fine.  Since I've installed Kubuntu, I think I remember following a howto on getting around blacklisted modules while installing my ATI driver where it was mentioned that some things would have to be re-installed every time I do a kernel update.  

So...do I need the new kernel version?  Do I want to new kernel version?  Can I remove it?  

Thanks for any help!

---

### Post by Brunellus on 2006-09-21
the kernel is the fundamental part of the operating system that deals with your interactions with the hardware. No kernel, no OS. The one showstopper in any OS is a kernel failure.

Most users won't need to compile their own kernels, ever.  If it's something you want to do, you're free to do so. But it's seldom necessary in practice unless you are a kernel developer or have very specific needs that are not met by the stock compiled kernels.

Your problems arise from ATI's drivers not playing well with the kernel...something that ATI needs to fix.  But since the drivers are closed-source, we can only wait for ATI to improve them.

offtopic:  thank you for spelling "kernel" right.  If I had a nickel for every time I've seen anyone--including long-time Linux users--write "kernal," I'd....err...I'd have a lot of five-cent coins.

---

### Post by madcow72 on 2006-09-21
Thanks!  Spelling is one of my (few) talents.

So...I should definitely stick to the earlier kernel then, and maybe try upgrading the driver at a later date?  How can I change the boot order in GRUB?

---

### Post by Brunellus on 2006-09-22
you can remove the offending kernel in synaptic, and simply refuse further kernel updates for now.

---

### Post by David Corrales on 2006-09-22
> 
1)  What exactly is the kernel?

The kernel could be thought of as the brain of an operating system. In the case of the linux kernel, it handles stuff like: memory management, network stack, process and thread management, drivers,etc.
> 
2)  I've found some howto's in my searches on other topics which mention having to download the kernel-source and compile it.  Is this something everyone needs to do?

People who need to download the kernel usually -need- something that isn't implemented in their current one. Usually newer drivers or fixes. The majority of people won't have problems with the packaged kernels.
> 
3)  I've noticed that recently there was a kernel update from Adept - why does one need to update the kernel?

Pre-packaged kernels are updated to patch security flaws found recently. Sometimes the patches bring the kernel up to a different version number, that's why you got 2 different kernels.
> 
4)  The reason I ask this last question in particular is what leads me to my specific question:  Yesterday I rebooted my computer and noticed that GRUB gave me a new choice of kernels to boot from, the new one and the old.  If I choose the new one the computer freezes when trying to enter X - I get a black screen and Alt+F2, CTRL-Alt-Backspace don't do anything.  If I choose the old kernel, everything works fine.  Since I've installed Kubuntu, I think I remember following a howto on getting around blacklisted modules while installing my ATI driver where it was mentioned that some things would have to be re-installed every time I do a kernel update.  

So...do I need the new kernel version?  Do I want to new kernel version?  Can I remove it?  

The problem you faced was because the driver wasn't yet compiled for the new kernel. Every time a kernel gets a number bump, you need to download it's headers in order to be able to compile modules for it.
If you want to use the new kernel, download it's header and follow the standard driver installation procedure.

---

### Post by madcow72 on 2006-09-22
Great!  Thanks for all of your help.  I'll try some of these things tomorrow when I get back to my work computer.

---

