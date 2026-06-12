---
title: "COMPIZ Not working on VMWARE"
date: 2009-10-30
forum: Apple Hardware Users
---

### Post by sameer0924 on 2009-10-30
I am an absolute starter. Please help. I was trying to use Compiz but I couldn't. This is what I get out of COMPIZ-CHECK

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         VMware SVGA II Adapter
 Driver in use:         vmware
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by maflynn on 2009-10-30
That's because you don't have the hardware accleration in a virtual environment. Only by booting up natively will you have compiz

---

### Post by rlsx on 2009-11-10
Note the following: I have tried both Ubuntu and Kubuntu 9.10, on Worktsation 7.0.
For Kubuntu, to enable visual effects, one is given the choice between "OpenGL" and "XRender". The former option doesn't work, but the second does work.

As I understand it, OpenGL is not (yet?) available for Linux guests in Vmware. Only for Windows guests.

The question that remains: I don't know what "XRender" is. But, can Ubuntu use that same technique/api that Kubuntu does, to implement visual effects?

---

