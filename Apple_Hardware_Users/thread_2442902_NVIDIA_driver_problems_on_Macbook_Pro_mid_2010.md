---
title: "NVIDIA driver problems on Macbook Pro mid 2010"
date: 2020-05-09
forum: Apple Hardware Users
---

### Post by nofrills2 on 2020-05-09
[COLOR=#242729][FONT=Arial]I´ve just installed Ubuntu 18.04 LTS on my Macbook Pro, and from the outset I had trouble with system stability. Eventually I narrowed the problem down to the nvidia drivers (card is an MCP89 Geforce G320). In software and updates I set the driver to proprietory and re-booted.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]On reboot the graphics are completely lost, all black. I need some stepwise help to dig myself out and get the drivers to work properly. Any help would be appreciated![/FONT][/COLOR]

---

### Post by daniewicz on 2020-05-10
Any reason you are not using the newer 20.04 release?

---

### Post by nofrills2 on 2020-05-10
I have another macbook pro mid 2010 laptop already running on 18.04, just trying to keep things consistent between the two. Maybe I should upgrade the other as well?

---

### Post by daniewicz on 2020-05-11
I think I would.

---

### Post by este.el.paz on 2020-05-13
> **nofrills2 said:**
> [COLOR=#242729][FONT=Arial]I´ve just installed Ubuntu 18.04 LTS on my Macbook Pro, and from the outset I had trouble with system stability. Eventually I narrowed the problem down to the nvidia drivers (card is an MCP89 Geforce G320). In software and updates I set the driver to proprietory and re-booted.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]On reboot the graphics are completely lost, all black. I need some stepwise help to dig myself out and get the drivers to work properly. Any help would be appreciated![/FONT][/COLOR]

@nofrills:

I have an '09 MBPro with Nvidia card . . . now running Manjaro, but I've had a number of distros on that machine . . . .  One thing that you didn't mention was using the "Additional Drivers" app that ubuntu provides . . . that lists the drivers that should be compatible.

6 - 8 months back I was having some issues with my '12 Mac Pro that I added an Nvidia card (GTX 780????) into to be able to get to Mojave . . . and I started having problems with "not reviving from suspend" . . . and some Sid based gurus suggested I go to proprietary Nvidia drivers . . . so I did that via the console . . . but started having "problems" when the Sid system was upgrading.  I posted a question on the Nvidia linux site and the guy did respond fairly quickly, but basically said, "Don't hold your breath, because your legacy card isn't really on our radar any more . . . ."

So I went back to "nouveau" on many of my distros, and I even went just "default" with an OpenSUSE install . . . I find that nouveau or default provide good video, and there aren't the "breakages" that showed up when Nvidia drivers weren't updating with the system . . . .  When in Rome, so to speak . . . I thought it was "better" to go Nvidia, but in linux I don't think Nvidia is "on it" . . . because linux is always upgrading in one way or another.

18.04 is now "old" in the linux world, but that isn't so old in the Nvidia world . . . .  But to the comment, why have different versions on different computers, it really isn't needed . . . you could have 18.04 on one and 20.04 on another . . . for the variety.  

e.e.p.

---

