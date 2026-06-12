---
title: "Only 25% RAM usage of 2gb running 11.04"
date: 2011-10-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Boris Dawa on 2011-10-10
My Ubuntu 11.04 32bit only uses around 25% of the available 2gb of RAM. The CPU is busy but the RAM stays at 20 - 25%. Can I get it to use more RAM than that and hopefully speed up the machine as it can be very sluggish? Asus Eee PC 1015PX, Atom N570.

---

### Post by SeijiSensei on 2011-10-10
> **Boris Dawa said:**
> My Ubuntu 11.04 32bit only uses around 25% of the available 2gb of RAM. The CPU is busy but the RAM stays at 20 - 25%. Can I get it to use more RAM than that and hopefully speed up the machine as it can be very sluggish? Asus Eee PC 1015PX, Atom N570.

Linux uses nearly all the RAM in a system.  If you run the "top" command, you'll see an entry called "cached."  This is a cache of all recently-used memory pages.  As more programs are started and require system memory, the cache shrinks as required.

There are some tuning parameters you can try to improve performance, "[swappiness]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F")" in particular.

Atom's aren't really known for performance, so I suspect there's a limit to how much you can do to improve things.  If you're experiencing issues with the graphical user interface, try turning off things like "desktop effects."

---

### Post by Lisiano on 2011-10-10
Linux, unlike Windows, uses the free space to cache files in memory. Pictures, programs, webpages, everything. The second you need more space, the cached stuff just gets removed.
Currently, I'm on a 8GB DDR3 RAM rig and using only 3.6GB, I would be using less if I didn't have a gig cached. Also I'm using KDE, one of the heaviest desktop environments.

As for the speed, don't be too hard on a netbook, it's CPU is not as fast as a laptops or a desktops. It's designed to work with only a few applications open. Also what is the CPU busy with, take a look at the output of the command ```
top
```
This will tell you what is using your CPU and also show you if your CPU is doing "I/O Wait", it might the reason for the sluggishness.

---

### Post by snowpine on 2011-10-10
In what way is your computer slow? Booting, launching apps, saving files, watching videos, calculating spreadsheets, etc... there are many different ways a computer can be "slow," each with a different solution. The terminal command 'top' will tell you what's clogging your CPU.

In general, RAM and CPU are two separate resources. And it is good that you are only using 25% of your RAM, because that means you have 75% free if you need it. :)

---

### Post by 2F4U on 2011-10-10
> **Boris Dawa said:**
> My Ubuntu 11.04 32bit only uses around 25% of the available 2gb of RAM. The CPU is busy but the RAM stays at 20 - 25%. Can I get it to use more RAM than that and hopefully speed up the machine as it can be very sluggish? Asus Eee PC 1015PX, Atom N570.

My guess would be that the bottleneck is the CPU rather than the RAM. Check what applications and services are running. It could also help to try a more lightweight desktop environment.

---

### Post by viperdvman on 2011-10-10
Pretty much in any netbook, the CPU is the bottleneck. Intel Atoms were designed to be ultra-portable and ultra energy efficient. Even my AMD V105 was modified from the K10 to be ultra-efficient *(though arguably more powerful than a comparable Atom)*. You're talking about a processor that only runs at 1.2-1.6GHz (1.0 for dual-core AMD C-50), better than a comparable Pentium-M based Celeron *(which was what the first netbooks were running before the Atom came out)*. You simply can't ask a netbook processor to do as much as even a Core 2-based Celeron. Memory usage may be great, but the OS and its apps are still going to require processing power. And with only 1.2-1.6GHz of power, you'll see 50-85% much more frequently than on your 2.0-2.5GHz laptop.

Unless you're running a dual-core Atom/C-series/E-series with NVidia Ion or ATI Radeon, I wouldn't try running too many things at once on a netbook, especially if you're watching YouTube videos or viewing any other websites that use Flash *(Flash is a big resource hog on ANY OS)*.

25% memory usage out of your 2GB... you doing just fine, trust me :) With Windows 7 Starter, you'd be running 35-50% easily, which is why most reviewers recommend you upgrade to 2GB on any Windows netbook.

---

### Post by Boris Dawa on 2011-10-11
Sorry, I forgot to use the quote reply, see below 

Thank you for the 'top' command, I found that very useful indeed. It seems things are working normally which is very encouraging. I think the CPU is the thing that is holding things back as far as speed goes.
Thank you so much for your help and for taking time to do that, I appreciate it very much.

---

### Post by Boris Dawa on 2011-10-11
Thank you for your answer and help, I really appreciate it. One question with the 'top' command, I cannot see the 'I/O wait' for the CPU, does that mean it is not using it and that it is ok the way it is?

---

### Post by Boris Dawa on 2011-10-11
> **SeijiSensei said:**
> Linux uses nearly all the RAM in a system.  If you run the "top" command, you'll see an entry called "cached."  This is a cache of all recently-used memory pages.  As more programs are started and require system memory, the cache shrinks as required.

There are some tuning parameters you can try to improve performance, "[swappiness]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F")" in particular.

Atom's aren't really known for performance, so I suspect there's a limit to how much you can do to improve things.  If you're experiencing issues with the graphical user interface, try turning off things like "desktop effects."

Thank you for the 'top' command, I found that very useful indeed. It  seems things are working normally which is very encouraging. I think the  CPU is the thing that is holding things back as far as speed goes.
Thank you so much for your help and for taking time to do that, I appreciate it very much.

---

### Post by Lisiano on 2011-10-11
I/O wait in top is xx.x%wa, where xx.x is some percent.
As a side note, you can use ```
iotop
``` to see what is using the HDD and how much.

---

### Post by Boris Dawa on 2011-10-11
> **Lisiano said:**
> Linux, unlike Windows, uses the free space to cache files in memory. Pictures, programs, webpages, everything. The second you need more space, the cached stuff just gets removed.
Currently, I'm on a 8GB DDR3 RAM rig and using only 3.6GB, I would be using less if I didn't have a gig cached. Also I'm using KDE, one of the heaviest desktop environments.

As for the speed, don't be too hard on a netbook, it's CPU is not as fast as a laptops or a desktops. It's designed to work with only a few applications open. Also what is the CPU busy with, take a look at the output of the command ```
top
```This will tell you what is using your CPU and also show you if your CPU is doing "I/O Wait", it might the reason for the sluggishness.

Thank you for your answer and help, I really appreciate it. One question  with the 'top' command, I cannot see the 'I/O wait' for the CPU, does  that mean it is not using it and that it is ok the way it is?

---

### Post by kurt18947 on 2011-10-11
It might well be worth trying Xubuntu or Lubuntu on your netbook though. I'm not sure if simply adding the Xfce-desktop or lubuntu-desktop would be as light as installing Xubuntu or Lubuntu without the gnome components or not.  I have an old notebook PIII 1Ghz. w/512 RAM which runs pretty well with Lubuntu & Chromium.  That is no more powerful than a netbook, and probably less so.  Task monitor shows 101 MB. RAM in use so yes, Linux seems pretty light on RAM usage; CPU seems to be limiting most often.

---

### Post by Boris Dawa on 2011-10-11
> **viperdvman said:**
> Pretty much in any netbook, the CPU is the bottleneck. Intel Atoms were designed to be ultra-portable and ultra energy efficient. Even my AMD V105 was modified from the K10 to be ultra-efficient *(though arguably more powerful than a comparable Atom)*. You're talking about a processor that only runs at 1.2-1.6GHz (1.0 for dual-core AMD C-50), better than a comparable Pentium-M based Celeron *(which was what the first netbooks were running before the Atom came out)*. You simply can't ask a netbook processor to do as much as even a Core 2-based Celeron. Memory usage may be great, but the OS and its apps are still going to require processing power. And with only 1.2-1.6GHz of power, you'll see 50-85% much more frequently than on your 2.0-2.5GHz laptop.

Unless you're running a dual-core Atom/C-series/E-series with NVidia Ion or ATI Radeon, I wouldn't try running too many things at once on a netbook, especially if you're watching YouTube videos or viewing any other websites that use Flash *(Flash is a big resource hog on ANY OS)*.

25% memory usage out of your 2GB... you doing just fine, trust me :) With Windows 7 Starter, you'd be running 35-50% easily, which is why most reviewers recommend you upgrade to 2GB on any Windows netbook.

Thank you for your very helpful advice which does make me feel better about the way my netbook is running.

---

### Post by clegends on 2011-10-15
Hi Boris Dawa, there is one more thing you could try. I'm running 11.10 (buggy baby... really buggy...) on my eeepc 901. I'm just about to upgrade to a 1015px as well. For the past couple years my netbook has been my main office machine... literally. Apart from our server, I do all my work on this machine. So I'm pretty excited about upgrading to a dual-core 570 cpu. Apparently there's not a huge improvement from the n450 single core models, but as I'm running currently an n270, the difference should be considerable.

Now, on with speeding up your netbook. Most of what everyone else has already said I'd agree with. Netbooks aren't designed for much more than surfing the net, and definitely (with an atom cpu anyway) not for outputting hd videos onto another device. I've found they are great for playing videos on their small screens, however. You've taken a great first step though by getting rid of windows, summarily useless for such a low resource powered device.

That said, when handled correctly, a netbook is an awesome device. I also upgraded mine to 2gb of ram, and found that I rarely need more than 1gb. My machine hardly ever runs over into the swap space with 2gb, however having 2gb *definitely* makes a huge improvement... there are just sometimes when it's needed.

The main thing I've done with my 901,and I'll do again next week with my new 1015px, is to upgrade the hard drive. My 901 came with a fairly slow 16gb ssd drive, which I upgraded to a runcore 64gb, and then later a kingspec 64gb ssd. The difference was immediate, and considerable. Instead of something usable only with a few applications, it has become a portable office, able to do everything I need. 

From memory, a 5400 rpm hard drive (what you'll have by default in your 1015px) has a read speed of around 50mb/s. The more recent ssd's (have just ordered a bulltproof 128gb from My Digital Discount) have a read/write speed upwards of 200mb/s. So yeah, 4 times faster means a noticeable difference.

A 128gb version will set you back a couple hundred dollars, but in my opinion is worth it. A 64gb model is half that. Please keep in mind though with the 1015px models there is no easy way to access the hard drive. While upgrading the ram is easy,from what I've read you will need to open up your machine to swap drives. It shouldn't be too hard, but keep in mind this is a great way to truly bork your machine if you're not confident with it. Will I be upgrading my drive when it comes next week? Definitely. Would I recommend a novice computer user to do the same? Entirely depends how adventurous you are, and whether you're willing to live with having stuffed up your machine if you make a big enough mistake. I knew next to nothing about hardware modding my machine a couple years ago, but that didn't stop my from trying. Good luck with it!

---

