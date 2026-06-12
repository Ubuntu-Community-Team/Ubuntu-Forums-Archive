---
title: "this keeps popping up...."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by adza on 2007-04-21
I keep getting this message when i try to install packages through the command line (probably is in synaptic as well, just don't get to see it :)) 


ldconfig: /usr/lib32/tls/libGL.so.1 is not a symbolic link


does anyone know what i need to link this to? Or what this may even be? any help would be great, i'm sure this is why stuff like gdesklets isn't working properly... ??

---

### Post by ffxr on 2007-04-21
libGL.so.1 is related to your openGL stack, i.e your 3D rendering library...

how did you install you graphics drivers? you could try reinstalling them.. for NVIDIA, i use the propriartory drivers instaled via the package available on the NVIDIA website.

---

### Post by adza on 2007-04-21
thanks ffxr, i have tried that however the package says that i can't be running xserver for the install... so i backed out at that stage....

---

