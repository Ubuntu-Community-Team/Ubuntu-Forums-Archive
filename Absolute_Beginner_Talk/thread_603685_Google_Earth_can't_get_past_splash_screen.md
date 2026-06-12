---
title: "Google Earth can't get past splash screen"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by machavillain on 2007-11-05
I know this is a common problem, but none of the threads seem to help me. I am using the ATI restricted driver; I also previously had GEarth working in Feisty before I formatted and started over....

---

### Post by machavillain on 2007-11-05
Any ideas on this? Anybody else having the same problem?

---

### Post by eluzi on 2007-11-05
Ubuntu Gutsy comes with Compiz by default, u sure u didn't install XGL for example ? Cos' it's got no compatibility with ATI... Check the following commands and post the output:

# fglrxinfo
< Should appear something like ATI MODEL, Version, etc...)

# glxinfo | grep render
< Shoul appear Direc Rendering: Yes >

If there's something different from this u should search it on Google cos' it's certainly 3d acceleration problems...

I've got a ATI X1300 Pro and it worked fine... Just stopped when I installed the 3d desktop features...

---

### Post by gadfly22 on 2007-11-05
I had this problem.  The solution that worked for me -- which you'll find in other threads I think -- involves adding libGL.so.1 and libGL.so.1.2 files from a previous ATI driver to the /usr/lib/googleearth file.

I'm at work right now, so I can't direct you better, but those threads (and there were more than one) are pretty easy to find.  And others have actually extracted the necessary files already, so the fix (if this is the right one) is pretty easy.

---

