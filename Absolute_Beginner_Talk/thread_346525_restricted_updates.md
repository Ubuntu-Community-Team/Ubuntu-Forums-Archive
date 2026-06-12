---
title: "restricted updates"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by ffpcs on 2007-01-25
Pentium III, nVidia TNT2 Pro PCI card, 256RAM, 80GIG HD
uname -r reveals version 2.6.15-27-386
The question is, what are the "restricted updates"? When I allow them to be installed, my system will not reboot and dies with a kernel panic - syncing error. Is there a trick to installing them properly? What do i lose by not installing them? Is the version I am currently on stable enough to just leave it as is?  Thanks - Frank

---

### Post by mikewhatever on 2007-01-28
Can you please specify where have you found restricted updates. Do you, perhaps mean kernel-restricted -modules, or restricted formats?

Seems to be resolved [http://ubuntuforums.org/showthread.php?t=346406](http://ubuntuforums.org/showthread.php?t=346406)

---

### Post by ffpcs on 2007-01-29
These were actually kernel updates that showed up automatically in the Update Manager window.  Previously, when I tried to install these updates, they resulted in my system being unable to boot.  I kept getting "kernel panic" errors.  Last night, however, I tried installing them one at a time, instead of allowing the Update Manager to install them all at once.  My intention was to try to identify WHICH of the updates was preventing my system from booting properly. For SOME reason (I have no idea why) THIS time (by installing them one at a time - I GUESS), they installed without incident.  From what I can tell, these "restricted" updates ALL had to do with my nVidia graphics adaptor.  The GOOD news is, since they installed, they SEEM to have fixed another problem I had with my system freezing up.  It used to freeze up if left idle for any length of time, but since the updates installed, that problem appears to have been fixed.  I'll let you know if that should change. I am so new to linux, I don't really have any faith in my skills yet.  I am just feeling my way along.

---

