---
title: "customize kernel"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by MicheleZ on 2007-02-12
Hello,

Apologies if the post is not using the "right" terminology.

I have installed Ubuntu 6.10 on my laptop and I got the (generic) 2.6.17.11?? kernel. 

Since I know the hardware specs of the laptop (an old Compaq Evo N610c) I would like to configure ubuntu specifically for it, i.e.
Pentium 4m 1800MHz processor,
ATI Mobility Radeon 7500 graphic card
W200 WLAN (orinoco based)
etc...

Do I need to compile a new kernel (something that scares me a bit since I am very new to Linux) or can I do it in a more simple way?

I wouldn't bother of course since it works fine, but until last week I had Ubuntu 6.06 installed on the very same laptop and it was much faster to boot up (now it takes 5 minutes from the time I have entered the password to the time the toolbars are populated).

Note that I do not have a CD drive or a floppy, so I performed a netboot: popping in the live CD and start the installer is therefore not an option.

Thanks for any help you can give me.

Cheers,

Michele

---

### Post by energiya on 2007-02-12
> **MicheleZ said:**
> 
Do I need to compile a new kernel (something that scares me a bit since I am very new to Linux) or can I do it in a more simple way?


If you're looking at tuning you kernel, you must compile it.

> **MicheleZ said:**
> 
I wouldn't bother of course since it works fine, but until last week I had Ubuntu 6.06 installed on the very same laptop and it was much faster to boot up (now it takes 5 minutes from the time I have entered the password to the time the toolbars are populated).


1800MHz proc. and 5 minutes of booting time!?!?! I have a AMD AthlonXP 1700+ (1473MHz I think) with 128MB RAM and used to start my PC in 40 sec. to GDM login and another 10 sec. to start Gnome. After compiling the kernel it takes 30 sec. to start the GDM screen and Gnome starts in the same timings (9-10 sec) .

If your want to compile a kernel, you should:
- know your hardware
- KEEP CURRENT KERNEL so that if something goes wrong you can still boot your PC
- depending on how much linux/computers you know, you may need to recompile a few times before getting the "perfect" config
- compiling takes 45-60 minutes on my PC but it varies (depends on you hardware/kernel configuration)

Hope I didn't discouraged you... I only have to say I'm compiling the kernel every time, now. You can reuse the settings file... so when you get it right, just backup you .config file

---

### Post by MicheleZ on 2007-02-12
Hey thanks for the quick reply.

I am not really discouraged but rather worried I will make all the classic beginner's mistakes and will be on this forum posting for quite a while :)

are you aware of any good how-to on the subject?

Cheers,

Michele

---

### Post by energiya on 2007-02-12
For ubuntu I used [this]("http://ubuntuforums.org/showthread.php?t=311158").

---

### Post by nickoli_02 on 2007-02-12
That startup time is pretty long. Is it just startup that is slow or is using ubuntu in general kind or sluggish? It's possible something is eating up system resources. At the terminal, type "top" to see if there are any processes hogging your resources.

---

### Post by MicheleZ on 2007-02-12
hi, 

thanks guys.
I re-installed and it seems to be ok now. So I bit the bullet and tried to compile the kernel (it is happening as I write...).

Just one last question (for this thread): is it the going practice on this forum to mark the thread as [solved] or something like this?

Cheers,

Michele

---

### Post by MicheleZ on 2007-02-13
Hello,

I did try to compile the kernel and I got this error message:

```
...
CC [M]  drivers/net/cassini.o
cc1: error: drivers/net/cassini.c: Input/output error
make[3]: *** [drivers/net/cassini.o] Error 1
make[2]: *** [drivers/net] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.17'
make: *** [debian/stamp-build-kernel] Error 2

```

Any clue on how to solve it?

do I need to provide more info?

Cheers,

Michele

---

