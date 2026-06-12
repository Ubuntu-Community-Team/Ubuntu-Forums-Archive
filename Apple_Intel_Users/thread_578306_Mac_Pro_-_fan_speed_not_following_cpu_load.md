---
title: "Mac Pro - fan speed not following cpu load"
date: 2007-10-17
forum: Apple Intel Users
---

### Post by nikitavfx on 2007-10-17
Hello everyone,

I got Ubuntu Gutsy running on a Mac Pro 8-core here. I also compiled a custom 2.6.22 kernel with the mactel patches. I'm very happy with the overall performance!

One thing though: fan speed. The default fan speed seems to be pretty low (although a little higher than on OS X) and every few minutes it increases for a minute than goes back to the default speed. The strange thing is: this is totally independent of the CPU load!!

When I run a CPU-intensive operation where all the cores are maxed out, the fan speed remains the same. The temperature (measured with coretemp) goes above 94 celsius which is where I abort the mission...

So how can I couple the fan speed to the cpu load?

I appreciate all help, thanks guys.

---

### Post by nikitavfx on 2007-10-17
Just found out something: the fan that turns up every few minutes is the one from my crappy ATI X1900 graphics card. So it's not the cpu fans that I'm hearing.

Still don't know how to make the cpu fans react to the load. I could potentially write a script that polls the temperature every few seconds and adjusts the fan speed but there must be a better solution out there!

---

### Post by jamieno10 on 2007-10-17
I am using a 8-core mac pro as well. I'm currently testing it. As a general question, what temperature would be considered 'ok'/safe?

I'm very interested in fan control as I'll be hoping to use as many as 7 cpus running numerical simulations.

Does anyone have any ideas on fan control in 7.10rc for macs???

---

### Post by jamieno10 on 2007-10-18
I understand that the module applsmc is able to control fan speed?

However, I find that for me (7.10rc), it is not loaded.

Doing sudo modprobe applesmc gives:

FATAL: Error inserting applesmc (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/applesmc.ko): No such device

The file /lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/applesmc.ko exists though.

help. Thanks!

---

### Post by nikitavfx on 2007-10-18
You need to compile a custom kernel to get that working. Just follow the instructions on this page, it worked for me!

[http://ubuntuforums.org/showthread.php?t=442941](http://ubuntuforums.org/showthread.php?t=442941)

When you do "make xconfig" search for applesmc and enable it.

There's one thing though that I couldn't get working, it seems to be a bug in the kernel (report has been filed): frequency scaling. The CPUs operate at 3GHz even when idle. This results in more heat than necessary. And this resulted in the higher fan rpms I posted about.

I've tested the Feisty and Gutsy (final) LiveCD as well, same result. No frequency scaling.

---

### Post by jamieno10 on 2007-10-19
Hi,

Thanks. You seem to be one of the few mac pro users on this forums.

Is there any difference between 7.10 final and 7.10rc?

The related (at least in terms of heat) issues of fan and scaling are worrying - especially the former - for me as I do numerical work on my mac pro. I tested things in Mac OS and the fans don't kick it as well and in fact, ubuntu seems keep it a little cooler (though not  by much). Looking at the apple forums, I get the impression that fan control is firmware based . Some users have upgraded/re-installed the SMC firmeware and problems have been reported.

Given that I'm a linux noob, I'm afraid that I'll break my current installation of ubuntu. What are the main differences between the patched and non-patched kernel?

I really hope the ubuntu developers will resolve these problems soon, and I think they probably will. 

Thanks!

---

### Post by cyberdork33 on 2007-10-19
> **jamieno10 said:**
>  Is there any difference between 7.10 final and 7.10rc? If you get any updates now, you have the full version. no need to reinstall anything

> Given that I'm a linux noob, I'm afraid that I'll break my current installation of ubuntu. What are the main differences between the patched and non-patched kernel?The mactel patches address several issues that are unique to Intel Macs. If you do not do a lot of customization to the default ubuntu kernel config (just make sure the applesmc stuff is enabled) then you won't have any problems. Besides, you retain the old kernel, and if you new kernel has problems, you just select the older kernel in Grub, and then remove the custom one.

---

### Post by nikitavfx on 2007-10-24
I've got 2.6.23 running with the mactel patches and the nvidia drivers on my Mac Pro. It was quiet a fight, but I took some notes and wrote up a howto.

[http://macprolinux.blogspot.com/](http://macprolinux.blogspot.com/)

The .config file I used for compiling the kernel is attached to the following post:

[http://ubuntuforums.org/showpost.php?p=3761856&postcount=11](http://ubuntuforums.org/showpost.php?p=3761856&postcount=11)

Let me know if this helps...

---

### Post by jamieno10 on 2007-10-24
This is really nice!

Thanks. Would have saved me loads of time if I've seen this earlier.

My mac pro is somewhat production ready now and I'm not too keen on messing about with GRUB considering I've had a number of difficulties with it. If I do try it, I'll let you know. 

The fan thing is annoying; I'm currently using smcfancontrol in OS X to set it to a high minimum fan speed (~1800rpm), which allows me to use up to 7 cpus and maintain temperatures ~59C (I think the max. temp is about 60-62 for the xeon cpus). 
The ability to use applesmc to set the fan speed in linux would have been much much nicer, but just afraid to mess up the installation now.

I was wondering if its possible to somehow just compile the applesmc module?

---

### Post by cyberdork33 on 2007-10-24
> **jamieno10 said:**
>  My mac pro is somewhat production ready now and I'm not too keen on messing about with GRUB considering I've had a number of difficulties with it. If I do try it, I'll let you know. 
You shouldn't have to touch the menu.lst file at all. Uninstall kernels the same way you install them (or use aptitude or apt-get) it will update the menu.lst to show only kernels that are actually available.

---

### Post by nikitavfx on 2007-11-13
> **nikitavfx said:**
> I've got 2.6.23 running with the mactel patches and the nvidia drivers on my Mac Pro. It was quiet a fight, but I took some notes and wrote up a howto.

[http://macprolinux.blogspot.com/](http://macprolinux.blogspot.com/)

The .config file I used for compiling the kernel is attached to this post.

Let me know if this is helping...

I've updated the .config file for the 2.6.23 Mac Pro custom kernel.

It seems, the legacy IDE drivers were not needed and did indeed cause some trouble with my wacom tablet (an IRQ conflict after about 10 minutes usage).

The new .config is attached to this message.

---

### Post by germay on 2007-11-19
Thanks a ton.

This is a greater bump.  Lots of info in this thread.

Mac pro 8 core 16gb ram running mental-ray presently using 14.6 gb of ram for mental-ray.

Without your help, my project would have taken the rest of the year to render with the AMD machine.
:guitar:

---

### Post by nikitavfx on 2007-11-20
> **germay said:**
> Thanks a ton.

This is a greater bump.  Lots of info in this thread.

Mac pro 8 core 16gb ram running mental-ray presently using 14.6 gb of ram for mental-ray.

Without your help, my project would have taken the rest of the year to render with the AMD machine.
:guitar:

Just curious, did you check the temperatures of your cores while rendering? Are you setting the fan speeds manually? If not, do you hear the fans speeding up under load?

---

### Post by cyberdork33 on 2007-11-20
> **nikitavfx said:**
> I've updated the .config file for the 2.6.23 Mac Pro custom kernel.

It seems, the legacy IDE drivers were not needed and did indeed cause some trouble with my wacom tablet (an IRQ conflict after about 10 minutes usage).

The new .config is attached to this message.

It might be a good idea to edit the first post of this thread and update it with your latest config. This will help people get to the correct version better.

---

### Post by germay on 2007-11-30
The temps are around 65 - 75 C.

How do you manually change the fan speed?

---

### Post by macaholic on 2007-12-02
Just curious, what issues does this specifically fix with Mac Pros? I read your blog post, and I already have sound, and accelerated rgaphics working, so what would be the advantage of doing this?

---

### Post by mert on 2007-12-07
I read this thread but its not clear to me of the fan speed problem is fixed on the mac pro.  does it still need to be set manually?

---

### Post by nikitavfx on 2007-12-08
As far as I know, the Mac Pro fan speed issue is not fixed. I had temperatures of 90 degrees celsius on all the cores after running CPU-intensive tasks. That is too much for my taste. I wrote a Python script that reads the core temperatures (you need to have the Macintel patches in the kernel or your temperature readings will be off!) and then sets the fan rpms manually.

Maybe someone figured out a better way?

By the way, saw that some of the macintel patches made it into the new kernel (release candidates). Let's hope that'll lessen our problems, once 2.6.24 is released...

---

### Post by mert on 2008-01-14
Does anyone know if fan speed control works 'out of the box' on MacPro machines now?  I'm thinking of putting Ubuntu on my 8-core MacPro workstation and I'd like to know beforehand what problems I'm going to run into.  The system boots from the Gutsy install CD but I haven't checked if fan speed changes in response to cpu load.  At least I don't hear the fans changing speed.

---

