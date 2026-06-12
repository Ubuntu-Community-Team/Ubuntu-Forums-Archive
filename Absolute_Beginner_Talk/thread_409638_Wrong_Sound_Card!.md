---
title: "Wrong Sound Card!"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-04-14
Hi:
I've noticed that when I installed Edgy, everything seemed to be ok, but have noticed that somehow, my Soundblaster Live 128 card is being identified as an Ensoniq AudoPCI.

How do I fix this?

I am trying to get midi output working so I can use it with music notation programs, and suspect this is why it is not working.

Thanks,
Ziffnabb

---

### Post by qamelian on 2007-04-14
Actually, this may be the same card. Creative owns Ensoniq and often market one card under two different brands. You midi problem is more likely caused by the need to load a soundfont so the card is able to play sounds triggered by midi data. In Windows, the Creative drivers automatically do this when you boot the PC. In Linux you need a utility to do this. Probably the simplest is awesfx, which you can find in the Ubuntu repos. Install it by typing in a terminal: ```
sudo aptitude install awesfx
```

While still in a terminal type ```
man awesfx
``` to see how to use it.

---

### Post by ziffnabb on 2007-04-14
I've installed awesfx. but when I try
man awesfx
I get
No manual entry for awesfx

Thanks,
Ziffnabb

---

### Post by qamelian on 2007-04-14
Try running awesfx with no parameters in a terminal window. It should at least display a help screen to show you what options can be used with it.

---

### Post by Loki-uk on 2007-04-14
You could try 

[http://www.aotk50.dsl.pipex.com/install-ubuntu-sb16/install-ubuntu-sb16.htm](http://www.aotk50.dsl.pipex.com/install-ubuntu-sb16/install-ubuntu-sb16.htm)

or have you looked at alsa?

[http://www.alsa-project.org/](http://www.alsa-project.org/)

Alsa have the SB128 listed as either an ES1370 or ES1371.

Loki

---

### Post by ziffnabb on 2007-04-14
When I try running awesfx in terminal, I get
bash: awesfx: command not found

Thanks
Ziffnabb

---

### Post by ziffnabb on 2007-04-14
When I try 

sudo modprobe snd-sb16

I get

FATAL: Error inserting snd_sb16 (/lib/modules/2.6.17-11-generic/kernel/sound/isa/sb/snd-sb16.ko): No such device

Thanks,
Ziffnabb

---

### Post by qamelian on 2007-04-15
> **ziffnabb said:**
> When I try running awesfx in terminal, I get
bash: awesfx: command not found

Thanks
Ziffnabb

Sorry, my bad. Here is a link to some documentation for the tools included in awesfx.
[http://www.alsa-project.org/~iwai/README-awedrv.txt](http://www.alsa-project.org/~iwai/README-awedrv.txt)

---

