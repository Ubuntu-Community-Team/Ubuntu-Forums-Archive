---
title: "Lamp Server"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-06-05
I wish to set up a Lamp Server and have found a number of promising tutorials to guide me along   I will use the 6.10 release since I understand it is not likely to fall over ...

I am proposing to drop a hard drive into an existing machine and install / test in that machine.  If it works and I do not mess up I would then propose buying a new motherboard and CPU and dropping the drive in there (so that I can return the existing machine to the user).

Is there any problem in doing this since the underlying hardware is going to be very different on moving the drive.  With Windows a repair install would fix any hal issues ..  but what with Ubuntu?

Has anyone experienced this at all?   I do not want to buy hardware until I know I have a working server (since I am good at getting things wrong and not being able to fix them).

---

### Post by pbw on 2007-06-05
It's easy to move your harddrive to a new box. I've done it a few times. Just make sure you have compiled support for the hardware into the kernel and edit grub to make sure the placement of root partition is correct. Possibly one or two other minor things you might have to tweak by hand depending, (like fstab).

---

### Post by expatCM on 2007-06-06
> Just make sure you have compiled support for the hardware into the kernel

erm....   yes ... but how please?

---

### Post by pbw on 2007-06-06
There's a ton of kernel howto threads and tutorials, no need to start another one here. However if you're unsure of how, i'd assume that you didn't roll your own kernel. In which case just use the generic (or server) kernel included with ubuntu, i'm sure you'll be fine.

---

