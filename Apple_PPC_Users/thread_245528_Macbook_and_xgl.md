---
title: "Macbook and xgl"
date: 2006-08-28
forum: Apple PPC Users
---

### Post by jafenske on 2006-08-28
I just bought my first mac and I have to say that I really like it. I do however miss Ubuntu, so I bought a copy of Parallels and it runs Ubuntu really well.  My question... Has anyone got xgl to work on the Macbook.  It seems like t should be possible and I have run through a couple of tutorials and I haven't managed to get it working.  

The tutorials I have used are
[http://bin-false.org/?p=17](http://bin-false.org/?p=17) 
and
[http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)

Once I get through the tutorials the x server fails to start.  I was hoping someone could offer me some advice.

Thanks

Joe

---

### Post by hajk on 2006-08-28
The answer you're looking for is in the specification of the Parallels virtual machine, not in the actual hardware of your MacBook. That's also why following any recipe/HOWTO meant for Ubuntu installation to a separate partition on the Mac HD is doomed -- it just won't work.

---

### Post by jafenske on 2006-08-28
So... If I really want xgl I'm going to have to use boot camp until parallels supports 3D accleration

---

### Post by bennyp on 2006-08-28
> **hajk said:**
> The answer you're looking for is in the specification of the Parallels virtual machine, not in the actual hardware of your MacBook. That's also why following any recipe/HOWTO meant for Ubuntu installation to a separate partition on the Mac HD is doomed -- it just won't work.

Hello! I've had the same issue, so I'm curious what you mean exactly by this message. Thanks for the clue.

---

### Post by hajk on 2006-08-29
Parallels mimics a computer in software, with (more or less) the following specifications:

1. Intel Celeron single-core processor.
2. Motherboard based on Intel 815 chipset.
3. VGA/SVGA graphics (VESA).
4. IDE drives.
5. RTL8029 Ethernet.
6. AC'97 compatible sound.
7. USB 1.1.
8. Standard PC keyboard.

This means that Ubuntu running in this VM has no access to features in the MacBook hardware that surpass the above specification: no dual core processor (so a SMP-enabled kernel is not needed); no 915 chipset; no ATI graphics (so no xgl/aiglx); no USB 2.0 and no Firewire. The galling thing is, of course, that  Parallels *itself* uses some sort of spinning Compiz cube to switch between full-screen VMs and OS X. 

The good news is that all the function keys (including NumLock on F6) retain their OS X functionality in the Parallels VM. And the two-finger touchpad scrolling function also works. I don't know about iSight, haven't tried that yet.  

I'm trying Ubuntu at present both in Parallels and installed separately on the HD -- the latter is definitely faster (possibly because it does use the dual cores), but then it has all sorts of problems with wireless and function keys.

---

### Post by bennyp on 2006-08-29
Very good, thanks for the detailed explanation. [It looks like the next version of parallels will have OpenGL support]("http://parallelsvirtualization.blogspot.com/2006/08/wwdc-wrap-up-part-2-vmware-is-in.html"). I wonder how they'll pull it off.

---

### Post by idn on 2006-09-02
I think someone got aiglx working which IMO is alot better than xgl, its less resource hungry, once my macbook pro can support aiglx im gonna make the switch

---

### Post by Christiaan on 2006-09-29
> **hajk said:**
> The galling thing is, of course, that  Parallels *itself* uses some sort of spinning Compiz cube to switch between full-screen VMs and OS X.
That's a system level GUI feature in Mac OS X (used, for instance, when switching between user accounts). Parallels is a Mac OS X application so it's no surprise it can do this.

---

### Post by hajk on 2006-09-29
> **Christiaan said:**
> That's a system level GUI feature in Mac OS X (used, for instance, when switching between user accounts). Parallels is a Mac OS X application so it's no surprise it can do this.

How true! I have installed the latest Parallels Beta, it's rumoured to have better graphics support, but I've not had the time yet to check this out.

---

