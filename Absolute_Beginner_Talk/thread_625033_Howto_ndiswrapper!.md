---
title: "Howto ndiswrapper?!"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by connydkt on 2007-11-27
Hi all,

this is a real newbe question...
I have just installed ubuntu onto my HP/Compaq NC6000 laptop, which worked fine.

No I am trying to get the WLAN working (Atheros chipset). I found following instructions for this:
[http://spaztech.wordpress.com/ubuntu-wireless-hp-nc6000](http://spaztech.wordpress.com/ubuntu-wireless-hp-nc6000)

Here I need to use the ndiswrapper, which I then downloaded from sourceforfe.net/projects/ndiswrapper
And now I am stuck... :confused:
When I do "make" it starts to do some things in the directory where I put the ndiswrapper files, but then I get a lot of errors:

loadndisdriver.c:15:20: error: stdlib.h: No such file or directory

I suppose I need to have the kernel source files or something to be able to compile this stuff?

Unfortunately I am a real beginner, my UNIX experience is a bot ago already, :(  so I would really appreciate if anyone would give me a hint what I am missing and what to do to get this working.


Thank you very much in advance!!!

Conny

---

### Post by caffienefree on 2007-11-27
ndiswrapper should be on your install disc. go to system>administration>synaptic package manager and search for it with your install disc in the drive.

---

### Post by connydkt on 2007-11-27
Hi caffienefree,

thanx for that - hmm, so simple... 

Now I continue to fight with the WLAN thing, somehow the net5211.inf is not sifficent, it looks for some ar5211.sys as well...
Anyway, thank you so far!

Cheers.

---

