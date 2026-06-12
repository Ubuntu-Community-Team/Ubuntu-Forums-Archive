---
title: "PC-BSD or OpenBSD?"
date: 2011-04-27
forum: Any Other OS
---

### Post by RichieB07 on 2011-04-27
I've been using Ubuntu for a while now and want to start looking at non-Ubuntu based OS's.  I really got looking at -BSD based OS's and have come across PC and Open.  Which one would be the best for a person just starting into the BSD world?  I know OpenBSD is more secure, but I've read that because of that security it's almost useless to the average user.  

I do also have PC-BSD already downloaded and on a CD.  It booted fine and worked perfectly with all my hardware.

Any tips on this, and any guides you know of to work from would be cool!

---

### Post by krapp on 2011-04-27
If your hardware is compatible with PC-BSD (which is usually the biggest hurdle prospective BSD users face) than great!

OpenBSD is getting ahead of yourself, however, if you skipped all the stepping stones so to speak that the range of Linux distros offers. Debian would be the next logical step up the ladder of complexity toward building a system by hand as OpenBSD would require, as you are probably already acquainted with Aptitude via the command line.

---

### Post by Buntumatic on 2011-04-27
My favorite is FreeBSD. I install it as I'd install Gentoo. After installing the bare base I sync the sources, rebuild the world with my own customized make.conf, install it, reboot and start building it from there. I find tailoring it for my hardware and software needs is tremendous fun.

---

### Post by Rubi1200 on 2011-04-27
If you are up for an adventure, try Arch:
[http://www.archlinux.org/](http://www.archlinux.org/)

---

### Post by MBybee on 2011-04-27
I use all 3 depending on the system, so I'll toss out the pros/cons:

FreeBSD - the Base OS. This one is pretty much the starting point for the others. It has a horrible installer, doesn't do anything for you by default, and supports everything really.

PC-BSD - FreeBSD + Customizations. This is a great starter OS to get your feet wet with BSD, and the dev team is *amazing*. Mailing list questions are answered super fast, and it's the only BSD that will boot you right to a fully working desktop... if it works at all. The downside is, if it does not support your machine, you're basically stuck with a broken version of FreeBSD.

OpenBSD - Most secure OS, quickest install I've ever seen on a BSD (like 10 mins or so, tops), and it will do most of the basics for you pretty quickly. Biggest hurdle - *no NTFS support* and *no VM support*. NTFS is coming soon, but unless you're on Current, I think you might want to wait for the next release (coming soon, IIRC). This one is my absolute fave, and I use it everywhere I don't need to run a VM (which I use Ubuntu for instead).

That help?

---

### Post by MasterTech515 on 2011-04-27
> **RichieB07 said:**
> I've been using Ubuntu for a while now and want to start looking at non-Ubuntu based OS's. I really got looking at -BSD based OS's and have come across PC and Open. Which one would be the best for a person just starting into the BSD world? I know OpenBSD is more secure, but I've read that because of that security it's almost useless to the average user. 

 
I would recommend FreeBSD.

---

### Post by kk0sse54 on 2011-04-27
> **RichieB07 said:**
> 
Any tips on this, and any guides you know of to work from would be cool!

The official documentation from all of the *BSD projects tends to be superb. Just depends on how much you're willing to read.

---

### Post by MBybee on 2011-04-27
BSD might actually be accused of being *over* documented. Daemonforums is also quite good, though fairly low traffic. Lots of good BSD focused sites out there.

---

### Post by RichieB07 on 2011-04-27
That certainly does help a lot.  Thanks everyone!

---

