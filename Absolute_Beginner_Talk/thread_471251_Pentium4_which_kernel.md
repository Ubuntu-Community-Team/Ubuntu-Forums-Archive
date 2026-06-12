---
title: "Pentium4 which kernel?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by jboehm on 2007-06-11
Hi,

I'm confused by the different options of the pre-compiled kernels.  I started out using the 386 version but read that this was really only of very old x86 processors.  Am I correct in thinking that I really should be using the *-generic kernel?

What is the *-lowlatency kernel?  This box  is a home theater PC.

Thanks,
Jon

---

### Post by insane_alien on 2007-06-11
generic is fine. 

low-latecy kernel is for ubuntu studio. if you are doing a lot of professional level audio recording straight to the PC then this would be a better option. otherwise it won't make much difference

---

### Post by bodhi.zazen on 2007-06-11
For you I would advise the generic kernel.

In terms of kernel you are on an i686

[http://en.wikipedia.org/wiki/I686](http://en.wikipedia.org/wiki/I686)

The Low lateny kernel is designed for sound, in particular MIDI devices, however performance takes a hit. Yo should not use this kernel unless you intend to use MIDI devices are are willing to take a performance hit.

[http://tonalsoft.com/pub/pitch-bend/pitch.2005-02-14.17-00.aspx](http://tonalsoft.com/pub/pitch-bend/pitch.2005-02-14.17-00.aspx)

---

### Post by p_quarles on 2007-06-11
I'm running the standard (i86) kernel on my old Pentium 4 desktop. It only has 384 MB RAM, so X started up kind of slowly, but apart from that it worked perfectly fine.

---

