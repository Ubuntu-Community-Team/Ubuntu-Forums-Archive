---
title: "Kernels, Kernels, Kernels...."
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-07-27
ahhh...just when I think I've got a grasp on Linux, there's something new to learn...:) 

I was thinking of installing a low latency kernel. What exactly is a kernel and say I do install the low latency kernel...will I have to choose it from the grub menu? How exactly does installing this particular kernel help me with recording music?

Thanks for any responses in advance...and my apologies if this topic has been regurgitated too many times...

---

### Post by Mornedhel on 2007-07-27
This is a kernel :

[http://en.wikipedia.org/wiki/Kernel_%28computer_science%29](http://en.wikipedia.org/wiki/Kernel_%28computer_science%29)

You can install multiple kernels and choose to boot one or another via GRUB (last time I did it, it was the default behaviour).

---

### Post by Foxmike on 2007-07-27
I don't know about low latency kernels (do you have any details?  I'm curious:)).  If you install it via synaptic/adept/apt, you should see it in GRUB upon next reboot.  If you compile it from source, then you will have to edit GRUB (/boot/grub/menu.lst) in order to access it.

---

### Post by noof on 2007-07-27
First of all, why do you think you need to install a new kernel? If you compile an own kernel you have to manually update it to new versions and compile your own driver-modules. I guess you can copy the config from the repo-kernel, else you have to find out which hardware you have and enable them which can take some time. I honestly don't think it's worth the time.

---

### Post by isaacj87 on 2007-07-27
I've been trying to use JACK and ardour to record music. I'm using a USB audio I/O (MobilePre USB) to receive the sound, but it seems as if my computer can't handle it...If I use the same set-up with a more bloated and heavier program on Windows it works fine. With JACK and ardour, I get choppy playback and I can barely overdub (the load/buffer or whatever seems to drop)...basically I can't really record well....

I read somewhere that using a low-latency kernel (I believe found in Ubuntu Studio) helps with the perfomance...

---

### Post by rillip on 2007-07-27
From the tenor of the pose, I think it's safe to say you don't know enough about kernels to be ready to compile one from source and have this turn out well.  If you're going to install from synaptic/apt-get, it's pretty straightforward, it shows up in your grub menu list.  

This is just a crude description, you can find better by googiling, but the kernel is effectively half of the operating system.  One half is the stuff you're used to, userland.  Program, like Gnome, Synaptic, Nautilus, etc. that provide core services are part of the OS.  The other half is kernelland.  The kernel is responsible for all hardware interactions, such as your keyboard, cd-rom, hard drives, monitor, etc.  If you've ever seen the 80's movie Tron, The Master Control Program is semi-analagous, though most kernels refrain from being evil megalomaniacs.

---

### Post by isaacj87 on 2007-07-27
I see, I know how to compile a kernel but I wasn't planning on doing so...the kernel is in the Ubuntu Studio repo. I had to download and install a firmware for my USB Audio device and I modified some udev rules...Would I have to repeat the process if I use the new kernel?

---

### Post by Foxmike on 2007-07-27
I don't think so.  Basically, if you update the kernel, the only thing you would have to update are video drivers.

---

### Post by coffeecat on 2007-07-27
> **isaacj87 said:**
> I see, I know how to compile a kernel but I wasn't planning on doing so...the kernel is in the Ubuntu Studio repo.

Don't go compiling your own kernel. Are you using Ubuntu or UbuntuStudio? The low latency kernel is in the Ubuntu repositories if you are using Ubuntu. Just install it via Synaptic and it will be added to your grub menu as other posters have said. I did the same myself - no problem.

And yes - you do need the lowlatency kernel for audio work.

---

### Post by isaacj87 on 2007-07-27
I'm using regular fiesty...

Do you know what particular package to install?

Is it linux-lowlatency?

---

### Post by coffeecat on 2007-07-27
> **isaacj87 said:**
> Is it linux-lowlatency?


Yes. That's a meta-package which will pull in what you need and will ensure that upgrades work. If that doesn't mark linux-restricted-modules-lowlatency for installation, you might want to install that too - that's if you're using proprietary video-drivers.

---

### Post by isaacj87 on 2007-07-27
Thanks...I'm download/installing as we speak...

I'll post if my situation doesn't improve. or (let's hope not) gets worse. :)

---

### Post by isaacj87 on 2007-07-27
Hmm...installed...works fine..but I don't really see any differences performance wise.

Is there anyway to make GRUB default back to the generic kernel rather than the lowlatency?

---

### Post by 11touche on 2007-07-28
Uh... by editing /boot/grub/menu.lst maybe

---

