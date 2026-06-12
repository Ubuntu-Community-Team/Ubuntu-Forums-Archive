---
title: "How comprhensive is Ubuntu"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Oddjob74 on 2007-03-26
I have a question about Ubuntu! I have recently installed it and have got the basics up and running. i.e. internet, messenger, email with evolution. However I am thinking about the longer term. I really like the OS and don't want to have to change back to Windows. I just need some assurance that there are programs about that will make certain things on my laptop work that are currently not. For example, I have a memory card reader built in to the laptop not working. S-video output and the graphic option to switch resolutions and outputs to TV etc. Webcam, and little things like the wireless button light not working although I am connected to the internet wirelessly!? :confused: If I was to stick with it whats the learning curve until I can sort all these things out? Cheers in advance! :)

---

### Post by digital_sabotage on 2007-03-26
I'm on Acer Aspire 5610 laptop ...can't get my internal ENE card reader working ...haven't found a solution yet ...my S-video works if i connect it to my tv first and then boot the computer ...can hot-plug it then but if i shut computer off then i have to follow the same procedure ...search ...search ...then search some more*L*  ...good luck ...i hope you stick with it:-)

---

### Post by FryerFox on 2007-03-26
Your odds are good that you will be able to get things working in one of three ways:

- You figure out the way to get your hardware working yourself (possibly by compiling some driver from source, and/or messing with a configuration file).
- Someone writes a good howto on this forum (or elsewhere)
- One day, an update appears that after installing, magically causes your wireless LED to start blinking. Drivers are being added every day to the kernel and the other components of Ubuntu. Every once in a while, updates are provided and things start to work that didn't before.

I personally have usually taken the second choice, but after some experience, I now feel quite comfortable with the first also.

It's worth sticking with it and learning Linux despite the steep learning curve.

---

### Post by macogw on 2007-03-26
What kind of memory card reader is it?  Can you put "lspci" in the terminal (no quotes, its under applications > accessories) and print the output.  If it's  a Texas Instruments SD card reader, I know how to fix it.  You put 
tifm_core
tifm_sd
tifm_7xx1

into /etc/modules (type "gksudo gedit /etc/modules" to edit the file)

---

### Post by chili555 on 2007-03-26
Many of the things you are asking about work now; maybe not on your particular computer and maybe not without tweaking a configuration file. I have working:
1. Memory card reader (I assume you meant like SD cards, etc. in digital cameras. That's the long way around, since I plug my camera's USB cord into my computer and a window pops up immediately "Import Photos?"

2. Webcam works with Ekiga just fine.

3. S-video to TV. I have to fiddle a bit with resolution, but it works. I agree, there should be a quik-n-EZ gui.

4. There are posts about "option LED=1" on the web that may or may not help your laptop's wireless LED.

All these things get better every day. Help is coming. A problem is that new stuff comes out in computers every week and the next day, you and I want all the volunteers who write drivers, kernels, packages, etc. for linux to come out with support for the cold beer dispenser on my new laptop.

---

### Post by MeeMaw on 2007-03-26
I'm sure you can get your internal card reader working..... and I have a camera card reader with a USB cord - it works just fine.....

I know you can't see a webcam with Gaim, but you can with Kopete because I'm watching my grandchildren right now.

Don't give up!!!

---

### Post by lamalex on 2007-03-26
for your tv, monitor hotplugging doesn't work yet. it's scheduled to be in Xorg 7.3 (after being deferred a few times so who knows.) Feisty +1 should theoretically support it. As for your LED, does that really matter?

---

### Post by FryerFox on 2007-03-26
> **Iamalex said:**
> As for your LED, does that really matter?

I say, let him have his LED! :)

Actually, it annoyed me to no end when I originally installed breezy and the LED didn't work. I got everything else working except for that LED - It didn't work until Dapper came out.

---

### Post by nickoli_02 on 2007-03-27
you guys have an LED that lights up when you're connected wirelessly?

aww, now I want one...

---

