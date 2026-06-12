---
title: "Checking CPUs"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Recked on 2007-04-06
Hello,

Just wondering if there is anybody out there who might be able to suggest a piece of software available to Feisty users that checks to see if cpus are functioning properly.

I am having a number of odd issues with my dual Athlon MP based desktop mainly with the boot process, not getting a bootsplash and now an error that could not be reported because according to Feisty (gnome) the issue is in the bios.

Any help would be appreciated.

thank you

---

### Post by crispy_420 on 2007-04-06
Dual processor system? Do you have the right kernel for the job?

---

### Post by Recked on 2007-04-06
Hey Crispy,

After doing the initial install that is the first thing I looked for in Synaptic, but all the SMP entries said something to the affect of "obsoleted.....blah blah etc." so I left the already installed kernel.

And yes my machine is a dual Athlon MP 2 gig processor machine, with 2 gig ram and an older Nvidia FX1000 AGP video card all mounted on a MSI motherboard.

Never had any issues before with this machine and I just replaced the motherboard. I checked bios and I don't see how there could be issues with it all of a sudden as the only thing I have changed recently is to diable the onboard audio chipset so the system only sees the SB Live soundcard.

System is not acting as it did when I had Edgy installed so I guess I am just assuming there is yet another issue.

thanks much for the help

---

### Post by Recked on 2007-04-06
I just checked again and kernel linux-k7-smp version 2.6.20.14.12 reads "Obsoleted by: linux-generic"

????

---

### Post by Patrick K on 2007-04-06
Obsoleted is correct. The generic kernel is what you want. It is the newer version and provides the proper services for both dual and single core chips.

---

### Post by Recked on 2007-04-06
Hi Patrick,

Thanks for that quick reply. Any way to explain:

system begins boot process

I see

Starting up......

Please wait

Screen goes blank/black (there is hard drive activity)

Login screen appears after 20 or so seconds

I log in

I get both panels, but the wallpaper is missing for the first few seconds then it appears out of nowhere

Sometimes I get a crash report icon in the system tray regarding usplash.

thanks

---

### Post by Patrick K on 2007-04-08
I wish I could help but I've not experienced your problem and don't have any solution. Hopefully, someone else will have some ideas. At least, this reply will bump it back to the top.

---

