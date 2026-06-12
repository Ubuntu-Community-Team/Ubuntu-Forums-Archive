---
title: "Quick Beryl question"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-22
Someone told me to run beryl $$ --replace and this is my result, what does it mean?? And how do I run beryl but make emerald put my windows boarders on?



Detected xserver : AIGLX 

Checking Display :0.0 ...

Checking for XComposite extension : failed

No composite extension
beryl: No composite extension

---

### Post by Sqwishy on 2007-07-22
Edit xorg.conf 

```
 sudo nano /etc/X11/xorg.conf 
```

at the bottom add

```

Section "Extensions"
       Option  "Composite"     "Enable"
EndSection

```

For emerald window borders, in xorg.conf the _"Screen" section_ add
```
    Option         "AddARGBGLXVisuals" "True" 
```

Oh, and when you're done, restart X with ctrl + alt + backspace

---

### Post by ukulele_ninja on 2007-07-22
I did that but it still deletes my frames when I run beryl and it wont let me use my keyboard....

I noticed all the things in Xorg have a little dot beside them except for the things I added so im wandering if I did it right.... this is so frustrating.

---

