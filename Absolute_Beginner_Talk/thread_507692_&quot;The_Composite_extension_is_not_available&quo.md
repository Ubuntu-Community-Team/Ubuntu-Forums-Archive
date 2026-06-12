---
title: "&quot;The Composite extension is not available&quot;??"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by kanati on 2007-07-23
Whenever I try to enable desktop effects this pops up "The Composite extension is not available".  I'm using the restricted ATI driver (x1950pro).  From what I've read the restricted driver is the problem and I need to replace it with something called Xorg.  I was following along in an earlier thread and got to here:

>  dan@dan-desktop:~$ glxinfo | grep direct
direct rendering: Yes
dan@dan-desktop:~$ cat /etc/X11/xorg.conf | grep Composite
        Option          "Composite"     "0"

That's when the thread got too technical and lost me.  Can anyone give me a hand with this?

---

### Post by tjpais on 2007-07-23
same problem with the x1650 card i use....does anyone know how to fix this?

---

### Post by njknight on 2007-07-23
I don't know if this is what you are after but I used to get that message when I first installed Ubuntu and solved the issue by installing the ENVY script and the correct drivers for the graphics card please see [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) which might be of some help. The script is for both ati and nvidia

good luck..and hope you get this solved.

---

