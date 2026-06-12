---
title: "LTSP unmount failing."
date: 2011-05-25
forum: Any Other OS
---

### Post by headvampyre@hotmail.co.uk on 2011-05-25
Hi,
Im attempting to install an LTSP server hosted off linux mint (Yes, its based off ubuntu, and uses ubuntu packages), but i have a problem:

I've managed to get past all the mirrors issues, but when i get to a certain point, ltsp-build-client gives an error:

Basically, it says that it cant unmount /proc as something it still in use.

I know this is because "/proc/sys/fs/binfmt_misc" is not being unmounted.

I've added "umount $ROOT/proc/sys/fs/binfmt_misc" (or something like that) to some of the build files(located in /usr/share/ltsp/Plugins/ubuntu(or wherever it is) but this repeatedly happens, and i dont know which files i need to place this in to fix the issue :(

Any help will be greatly appreciated.

---

### Post by Perfect Storm on 2011-05-27
Moved to Other OS/Distro Talk.

---

### Post by juancarlospaco on 2011-05-27
A few months ago i tried an LTSP for a cybercafe, it dont perform as i expected,
the main fact is that using an NX client/server was better than the whole LTSP sytem,
and less complex, it can play fullscreen HTML5 videos, smooth and easy.   &#664;&#8255;&#664;

---

