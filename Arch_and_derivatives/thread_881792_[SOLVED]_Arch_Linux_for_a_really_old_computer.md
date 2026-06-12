---
title: "[SOLVED] Arch Linux for a really old computer"
date: 2008-08-06
forum: Arch and derivatives
---

### Post by fenT1 on 2008-08-06
Hello,

I reciently bought a HP Omnibook xe2 for $20!. Because the guy tried to install win xp on it and ruined his win 95 partition.
This bargain has 4.9 Gig HD 191 MB Ram, it currently has Gutsy installed and it runs a litlle slow but it gets by.I would like to know if Arch linux would deliver a better performance on it since it was recommended in an earlier [thread]("http://ubuntuforums.org/showthread.php?t=872910")

---

### Post by tuxxy on 2008-08-06
Have you thought about an xubuntu install as thats better suited to older hardware.

---

### Post by blazercist on 2008-08-06
arch + gnome would eliminate some unneeded overhead but not much, you should think about using a different WM, something light like xfce, *box, etc.

---

### Post by ynnhoj on 2008-08-06
what sort of processor does the machine have?  if it's not i686, i guess you wouldn't stand to gain anything by running arch.  even a trimmed down *buntu install running a lighter window manager ought to get the job done.

but if you're looking to try something new, arch is easy enough to get installed.  a debian install would also be worth considering, particularly if you find that you prefer apt to pacman.

---

### Post by mips on 2008-08-06
Arch+Openbox or another light WM of your choice will run fine.

Look at Kmandlas blog for a list of good lightweight apps to go with it.

---

### Post by morgan141 on 2008-08-06
> **ynnhoj said:**
> what sort of processor does the machine have?  if it's not i686, i guess you wouldn't stand to gain anything by running arch.  even a trimmed down *buntu install running a lighter window manager ought to get the job done.

Unless I'm missing something, and I'm by no means an expert, if the processor isn't i686 then arch won't run on it at all. It is the equivalent of trying to run the x86_64 version on a 32bit processor. There was a project a little while back for i386 processors but I believe it is dead.

---

### Post by cardinals_fan on 2008-08-06
> **tuxxy said:**
> Have you thought about an xubuntu install as thats better suited to older hardware.
Eh?  Arch is lighter than Xubuntu...

---

### Post by Rumor on 2008-08-06
As others have noted, so long as the processor is a Pentium II or better, you should be able to install Arch. I have it running on an old Dell PII/233 with 128 RAM laptop using fluxbox for the window manager. It's no racehorse, but is a perfectly usable machine.

---

### Post by fenT1 on 2008-08-06
> **ynnhoj said:**
> what sort of processor does the machine have?  if it's not i686, i guess you wouldn't stand to gain anything by running arch.  even a trimmed down *buntu install running a lighter window manager ought to get the job done.

but if you're looking to try something new, arch is easy enough to get installed.  a debian install would also be worth considering, particularly if you find that you prefer apt to pacman.

Thank you all for your input. My processor is Pentium 2. And yes i'm looking for something new and in the thread link before it was recommended for computer science needs.

---

### Post by mips on 2008-08-06
[http://translate.google.co.za/translate?hl=en&sl=it&u=http://it.wikipedia.org/wiki/I686&sa=X&oi=translate&resnum=6&ct=result&prev=/search%3Fq%3Di686%2Bwikipedia%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DFo8](http://translate.google.co.za/translate?hl=en&sl=it&u=http://it.wikipedia.org/wiki/I686&sa=X&oi=translate&resnum=6&ct=result&prev=/search%3Fq%3Di686%2Bwikipedia%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DFo8)
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#Pre-Installation](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#Pre-Installation)

---

### Post by K.Mandla on 2008-08-07
> **fenT1 said:**
> I reciently bought a HP Omnibook xe2 for $20!
Like this one?

[http://www.ciao.co.uk/HP_OmniBook_XE2__17163](http://www.ciao.co.uk/HP_OmniBook_XE2__17163)

Lucky!
> **tuxxy said:**
> Have you thought about an xubuntu install as thats better suited to older hardware.
Blech. If it's a Pentium II, Xubuntu will probably mope along like a depressed teenager. Or at least, in my opinion it would. ... :roll:
> **blazercist said:**
> arch + gnome would eliminate some unneeded overhead but not much, you should think about using a different WM, something light like xfce, *box, etc.
+1. Has anyone else noticed that Arch + Gnome is good, but once you put in the somewhat-required Gnome extras, you're back to sluggish again? Maybe it's just me. Maybe I need to eat less sugar. :shock:

---

### Post by Rumor on 2008-08-08
> **K.Mandla said:**
> Has anyone else noticed that Arch + Gnome is good, but once you put in the somewhat-required Gnome extras, you're back to sluggish again? Maybe it's just me. Maybe I need to eat less sugar. :shock:

It might be interesting to see the difference in resource usage between vanilla Gnome and Gnome with the bells and whistles. 

I have used Arch with Gnome+ on a pair of PII's, but they were "beefier" than the laptop in this thread. They were both running around 4-500 MHZ and had 512 RAM, so Gnome with the extras ran fine on them.

---

### Post by ch_123 on 2008-08-20
> **Rumor said:**
> As others have noted, so long as the processor is a Pentium II or better

I think its more like a Pentium Pro or better, then again, very few people would have a Pentium Pro PC, they were mainly used in servers due to their cost.

---

### Post by MisfitI38 on 2008-08-20
Arch+LXDE is a good starting point.

---

### Post by Calmatory on 2008-09-16
> **tuxxy said:**
> Have you thought about an xubuntu install as thats better suited to older hardware.
Just to let people know: Actually, then ONLY difference I saw was the decreased memory usage when I went from Ubuntu to Xubuntu. Sure Xubuntu has lighter default apps, but afterall the machine felt just as slow with Xubuntu as it did with Ubuntu. Actually, Windows XP was faster. :)

333 MHz Celeron with 256MB of RAM.

---

