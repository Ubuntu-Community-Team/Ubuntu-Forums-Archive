---
title: "Gutsy installed from livecd won't boot on my B&amp;W"
date: 2008-01-27
forum: Apple PPC Users
---

### Post by heroes_on_a_half_shell on 2008-01-27
hey guys,

this is my first post on the forums, because you guys are awesome and have already answered all my other questions thus far.  however, it seems like this hasn't happened before:

1. i installed xubuntu gutsy on my b&w g3 from the livecd with no issues except for the fact that i had no taskbar.  however, i didn't think i would need it and since i've already encountered/fixed that problem before, i just moved on.

2. install went smoothly

3. the system then restarted (after install) but never actually booted from the hard drive

4. i can still boot from the livecd

5. at this point, booting from the livecd gives me a taskbar

however, i dont know what i can do to rectify the situation once i get this far

any help would be greatly appreciated

---

### Post by heroes_on_a_half_shell on 2008-01-27
just to clarify, when i start up the machine w/o the livecd, absolutely nothing happens.it's as if there is no os on the hard drive

---

### Post by stream303 on 2008-01-27
I would definitely recommend the "alternate" install cd instead of the live one.  Many seem to get much further than the livecd sometimes.  

Have you checked out these two faqs:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Give that a shot and lets see how it goes.  I always thought the B&W looked cool.  Which one do you have and how much memory is installed?

---

### Post by heroes_on_a_half_shell on 2008-01-27
alright, i'll try an alternate cd install, but with the exception of not having a taskbar, the livecd seemed to work perfectly.

i'm running a 400Mhz B&W with the 2 devices per ide channel option and a currently unknown amout of ram - forgot to check when i had the livecd up -- all i know for sure is that i have a 128, a 256, and two unknown capacity sticks installed.

thanks for the reply

---

### Post by heroes_on_a_half_shell on 2008-01-27
well, i just finished installing from the 7.10 alternate cd, and i'm impressed.  it's perfect. with the exception that i can't seem to set the resolution higher than 832x624 and the picture doesn't fit correctly on my 17" crt monitor that's 1024 x 768 @ 85 Hz.

---

### Post by stream303 on 2008-01-28
Ok, lets see if we can take the easy route before trying to edit the /etc/X11/xorg.conf file.

Can you run
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and see if you can now set res to 1024x768?

If you know a few more details, you can try it without -phigh:
```
sudo dpkg-reconfigure xserver-xorg
```

There's also some good info here which my help with xorg settings even though it mention G3 iMac:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by heroes_on_a_half_shell on 2008-01-28
no dice stream,

all i got was several lines of:

FATAL: Module battery not found.

and no, i really don't know any details, i'm just starting out here -- i'm in the process of beginning to switch out all my computers to ubuntu/other distros -- my main rig is next.

i don't really have time to check out the known issues site tonight -- i'll get back with you later.

thanks again

---

