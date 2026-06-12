---
title: "Graphics issues with Xgl"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by icelechi on 2007-10-10
Hi,
I tried to enable desktop-effects but I got this message:

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

I use an HP Pavilion dv2617us
Graphics Card: Intel Graphics Media Accelerator X3100.

The hardware is obviously capable of handling it, but I don't know what to do from here.

PLEASE HELP!!

Thanks

---

### Post by defrex on 2007-10-10
The problem is that your graphics card has a bug that's been deemed to much to enable by default. It's an annoying video playback bug. I use it anyway though, personally.

1. Hit alt+F2
2. enter: gksudo gedit /usr/bin/compiz
3. Type your password
4. comment out (add # in front of) "T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965" (it should be line 60)

Then run compiz again.

---

### Post by icelechi on 2007-10-15
Thanks a lot.
Whew
No point in having high performace graphics hardware and not using it :)

---

