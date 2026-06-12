---
title: "[SOLVED] Fluxbuntu alternate CD wont boot"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by MangasColoradas on 2007-12-26
I see some people were having problems with the live CD but mine is the 'install' CD and it boots on my laptop but not my PC?

The boot order on both systems is the same and all other install CDs boot fine on my PC.....:confused:

I have been using Gnomebaker to burn at 4x and even 2x, I was wondering if there is a burning app that would let me 'force' the CD to be bootable?

It is just totally weird that it works on my laptop and all other bootable's work on  my PC....so that means its not the disc and its not my PC that has problems either...?

---

### Post by kpkeerthi on 2007-12-26
I faced the same issue. Booted with my laptop but no go with my desktop (got tired and installed arch). I read somewhere that if you burn the image onto a DVD it works fine but I did not try it for myself.

---

### Post by candtalan on 2007-12-26
I have sometimes found that the boot order does not always play nice. I would have usually put the floppy first (if it exists....) then cdrom then HD but some machines did not work then for boot CDs (!) I had to put the cdrom really up front before everything, then this sort of machine booted from cd.

Another thought - does the problem machine boot from *any* cd? does the cd drive work well, is it aged maybe? Also some cd drives are not good at reading some burned media - certainly this used to be true some time ago, not sure if it still happens?
good luck

---

### Post by kpkeerthi on 2007-12-26
Yeah. My desktop's is infact 5 year old. Nevertheless, it boots arch, feisty CD that I burned myself.

---

### Post by antmenj on 2007-12-26
If you start into this thread at about page 36 it seems a known issue.

[http://ubuntuforums.org/showthread.php?t=581033&highlight=fluxbuntu+boot&page=36](http://ubuntuforums.org/showthread.php?t=581033&highlight=fluxbuntu+boot&page=36)

I grabed a copy a wile back and it wouldn't boot for me so I shelved it then.  Seems a extra boot disk is needed sometimes.  At the time I downed a boot disk image but never worked out how to use it.

Hope to have another go however.....

---

### Post by MangasColoradas on 2007-12-26
> **candtalan said:**
> 

Another thought - does the problem machine boot from *any* cd? does the cd drive work well, is it aged maybe? Also some cd drives are not good at reading some burned media - certainly this used to be true some time ago, not sure if it still happens?
good luck

"all other install CDs boot fine on my PC"-from my post. ;)

Thanks Antmenj, I will have a read of that.
:)

---

### Post by MangasColoradas on 2007-12-26
> **kpkeerthi said:**
> I faced the same issue. Booted with my laptop but no go with my desktop (got tired and installed arch). I read somewhere that if you burn the image onto a DVD it works fine but I did not try it for myself.

Tried it on a DVD, no joy.

---

### Post by louieb on 2007-12-26
Same here on a P2-400mHz, 384MB ram. Boots to the point of trying to display the 1st  menu then video weirds out (don't know any other way to describe it). I did put it on another machine - so it seems the Fluxbuntu install disk is picky about what machines it will work on. 

BTW: the P2 now has PCFluxboxOS  - Its pretty nice. Just not Ubuntu based.

---

### Post by MangasColoradas on 2007-12-26
Hmm, mine doesnt even do that. The disc spins like it is going to boot from it, then I see my grub menu.

Works perfecly in the damn laptop. ;)

---

### Post by MangasColoradas on 2007-12-26
I really want this on my PC, would a USB drive work, I wonder?

---

### Post by MangasColoradas on 2007-12-27
I got it working by using Magiciso on Windows.

I extracted the boot file from the CD then added it to the original iso, saved it and then burnt it. I dont know why that worked but it did. :)

I assume that is easy to do on Linux so I will mark this thread solved.

---

