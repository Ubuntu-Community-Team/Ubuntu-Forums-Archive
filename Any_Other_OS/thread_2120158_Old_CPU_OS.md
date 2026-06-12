---
title: "Old CPU OS?"
date: 2013-02-25
forum: Any Other OS
---

### Post by tahdas on 2013-02-25
Im looking for a good *stable* light OS for my old CPU. 

I tried puppy, it ran well but i didnt like the look. I tried bodhi but it was too unstable. How bout [http://sparkylinux.org/?](http://sparkylinux.org/?) Is that any good?

---

### Post by tgalati4 on 2013-02-25
Give linux mint 14 mate a spin.  It works well on older hardware.

---

### Post by JiuJitsu500 on 2013-02-25
ArchBang runs very well on an old laptop I have, so does some old slackware variants I've tried on it. Arch is a little easier to use though, so I stuck with that.

Haven't tried sparky...

But from what I can give you, Debian for me is the easiest to use (any variant - knoppix spin-ofs with GUI's are VERY light and debian-based and run on damn near anything.

Arch and slackware light distros are a little more difficult, but use OpenBox or as "heavy" as LXDE and you shouldn't have an issue - arch and slackware are very light in what distros are spun out of them (not all of course, but most are pretty lightweight since their mostly rolling-releases).

Gentoo and it's variants are extremely difficult for newer users - but give you absolute control of literally everything - all at once at install too (not like others don't, but this is serious about no-autoconfig stuff). Sabayon is heavy, but other Gentoo can be as light as you want it.

Or, Damn Small Linux is very, very light... but you'd better be comfortable with the CLI.

I choose Arch for old computers - ArchBang specifically because you can run it on a cpu powered by a couple hamsters on an exercise wheel and a potato battery.

Most of what you'll worry about is the GUI apps and Desktop Environment though, linux itself requires almost nothing to run. MATE and Cinnamon are pretty light too - but forks of GNOME so they take a wee bit more. Razr is even lighter than LXDE - OpenBox is even lighter, Awesome is even lighter... Unity or KDE are heavy and intensive - GNOME or even it's fallback are not much less than that - if any depending on distro...

That's my two cents :) I like ArchBang man, so I'm biased I guess

---

### Post by tahdas on 2013-02-26
Is there a light os that looks kinda like mac?

---

### Post by addegsson on 2013-02-26
> **tahdas said:**
> Is there a light os that looks kinda like mac?

Try elementaryos, it's light and looks like mac:

[http://elementaryos.org/](http://elementaryos.org/)

---

### Post by tahdas on 2013-02-26
That wouldnt run i did try it.

---

### Post by Dry Lips on 2013-02-26
What kind of CPU do you have? And how much RAM?

---

### Post by tahdas on 2013-02-26
I think around 1 GB, its a dell from 1999.

---

### Post by UltimateCat on 2013-02-26
You could try one of these 6 to choose from:

[http://www.makeuseof.com/tag/6-lightweight-linux-distributions-give-pc-lease-life/](http://www.makeuseof.com/tag/6-lightweight-linux-distributions-give-pc-lease-life/)

Peppermint Linux is a nice distro too-
[http://www.expertreviews.co.uk/general/1289197/top-5-lightweight-linux-distros-for-older-pcs](http://www.expertreviews.co.uk/general/1289197/top-5-lightweight-linux-distros-for-older-pcs)

And Damm Small Linux
[http://www.osnews.com/story/24936/Damn_Small_Linux_Still_Damn_Fun](http://www.osnews.com/story/24936/Damn_Small_Linux_Still_Damn_Fun)

---

### Post by tahdas on 2013-02-26
I tried all the of those except damn small, i didn't really like any of them.

---

### Post by y6FgBn)~v on 2013-02-26
Have you tried [MacPup]("http://macpup.org/")?

---

### Post by tahdas on 2013-02-26
Yup.

---

### Post by mips on 2013-02-27
Can you post the output of

```
cat /proc/cpuinfo
```

&

```
free
```

here.

---

### Post by tahdas on 2013-02-27
tahdas@PepperMintIcecream ~ $ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 9
microcode	: 0x21
cpu MHz		: 2793.359
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips	: 5586.71
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:


and


tahdas@PepperMintIcecream ~ $ free
             total       used       free     shared    buffers     cached
Mem:       1534944     686736     848208          0      35464     373420
-/+ buffers/cache:     277852    1257092
Swap:      1562620          0    1562620


Right now im running peppermint, if i can get my internet card thiny working then im goingt to stick with that. Does anyone know how to remove the black box around cairo dock?
I got it removed but now i cant get it to apear when i mouse over were it should be.

---

### Post by mips on 2013-02-27
That PC cannot be from 1999 as it has hyper-threading, 2002 the earliest.

> flags: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss **ht** tm pbe up pebs bts cid xtpr

You also have 1.5GB of RAM

Your PC should run anything up to XFCE just fine and maybe even MATE.

---

### Post by Lisiano on 2013-02-27
In my school, we have a concert laptop which is uber slow. I don't remember the specs off my head but it is _definitely_ worse than yours. It's running Lubuntu atm and is quite snappy. I guess any LXDE or XFCE based distro will work quite well on yours. Gnome 2/Mate should also work fine. But if you want something even lighter, Damn Small Linux is quite lightweight.

---

### Post by tahdas on 2013-02-27
Well it wouldnt run Lubuntu for some reason. And now that i look again its from 2004. Right now im running peppermint which is fine for me for now. Maybe latter i try to install lubuntu again. Has anyone used Funduntu ([http://www.fuduntu.org/](http://www.fuduntu.org/)). It looks neat.

---

### Post by unheeding on 2013-02-27
> **tahdas said:**
> Well it wouldnt run Lubuntu for some reason. And now that i look again its from 2004. Right now im running peppermint which is fine for me for now. Maybe latter i try to install lubuntu again. Has anyone used Funduntu ([http://www.fuduntu.org/](http://www.fuduntu.org/)). It looks neat.

Fuduntu is good stuff.  It's RPM-based, so there is a little bit of a learning curve (you use yum instead of apt-get).  It also uses GNOME2, which is less resource heavy than GNOME3, but uses more memory/CPU than things like LXDE/XFCE.

Fuduntu also comes with tweaks to maximize battery life, which is nice.  The functionality is easy to replicate on Ubuntu, it involves [moving tmp/logs to ram](http://www.fewt.com/2010/07/move-your-logs-and-temp-files-to-ram.html), installing [laptop-mode-tools](http://samwel.tk/laptop_mode/) and tweaking it, and [changing your swappiness to 10](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)



Edit:  

Also, for older computers, [Haiku](https://www.haiku-os.org/) is a pretty great OS.  It's based on BeOS, and is super fast.  It's still in alpha, and there's not a lot of applications available for it, but it's awesome nonetheless.

---

### Post by tahdas on 2013-02-27
Ok I live booted fuduntu, I liked it but it was a little slow.

So what do you think, fuduntu or stick with peppermint and which will run better?

---

### Post by unheeding on 2013-02-27
Peppermint will probably give you better performance, but you should be able to run Fuduntu.

---

### Post by lykwydchykyn on 2013-02-28
A P4 with 1.5 GB of RAM is not so old that you should mess with a lot of super-tiny distros.

If "medium-light" distros aren't performing well, it's probably a graphics chip issue.

What's the output of:
```

lspci |grep -i vga

```

Honestly, if this was my machine, I'd quit distro hopping, install a minimal install of Debian/Ubuntu/[insert-general-purpose-distro-here] and just try different desktop environments until one of them pops.

---

### Post by tahdas on 2013-02-28
tahdas@PepperMintIcecream ~ $ lspci |grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

Yeah i think im going to stick with Peppermint for now, but id like to have it look mac-e or at least have a Ubuntu like top thingy (You know the thing at the of the screen with the time and mail and notifications.) I'd also like to have the x and minimize button for the browsers on the left instead of the right.
Thanks for the help and the advice!
tahdas

---

### Post by lykwydchykyn on 2013-03-01
> **tahdas said:**
> tahdas@PepperMintIcecream ~ $ lspci |grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

Just so happens that I've been wrestling with a machine with this very chipset today.  The older 800-series intel chips have been really poorly supported for the last several years.  With an 865 you're fortunate if X11 even works.

> 
Yeah i think im going to stick with Peppermint for now, but id like to have it look mac-e or at least have a Ubuntu like top thingy (You know the thing at the of the screen with the time and mail and notifications.) I'd also like to have the x and minimize button for the browsers on the left instead of the right.
Thanks for the help and the advice!
tahdas

You can customize this sort of thing in most desktop environments, I'd say start with XFCE and just dig in.  Don't be put off if the default look & feel isn't what you want, most desktop environments allow for pretty deep customization (Unity is probably the biggest exception).

---

### Post by str8bs on 2013-03-02
> **lykwydchykyn said:**
> A P4 with 1.5 GB of RAM is not so old that you should mess with a lot of super-tiny distros.

If "medium-light" distros aren't performing well, it's probably a graphics chip issue.

What's the output of:
```

lspci |grep -i vga

```

Honestly, if this was my machine, I'd quit distro hopping, install a minimal install of Debian/Ubuntu/[insert-general-purpose-distro-here] and just try different desktop environments until one of them pops.

Excellent point. IMO many often jump to "light" distributions based on presumption of CPU power when the graphics are what is eating all the CPU. And sadly, many follow the bad advice of downloading a so called "correct" xorg.conf from the net that turns a decent GPU into a snail. Good GPU performance can make a night and day difference. If your current GPU isn't well supported or can't be tweaked for improvements, even a cheap $5 - $15 used card can make a huge difference.
I have a Pentium-D with a measly Nvidia 6800 that runs the "fat as it gets" KDE quite well.
For "mac-e" I would go XFCE plus [GLx-Dock]("http://www.glx-dock.org/").

---

### Post by tahdas on 2013-03-05
[ATTACH=CONFIG]239819[/ATTACH]This is what i ve done so far.

---

