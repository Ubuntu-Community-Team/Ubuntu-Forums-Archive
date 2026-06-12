---
title: "scroll mouse doesn't scroll"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by tonyp1969 on 2008-04-19
HI,

I have just installed Ubuntu version 8.04 and it is great, everything seems to be a lot more user friendly. One thing that has always annoyed me about Ubuntu is the inability to use the scroll wheel on my mouse. I have a standard Microsoft optical scroll mouse. Any help with getting this working would be much appreciated.

Thanks

---

### Post by T-Virus on 2008-04-19
Hi Tony,

Looks like your xorg.conf file lacks one line. Open /etc/X11/xorg.conf as root:

```

sudo kate /etc/X11/xorg.conf

```

EDIT: Oh, if you're on Gnome replace **kate** with **gedit**

Find the mouse section it should have identifier such like this:
Identifier	"Configured Mouse"

Add the line:

```

Option		"ZAxisMapping"		"4 5"

```

before the EndSection.

Now restart X server (Ctrl + Alt + Backspace) and mouse wheel should be working.

---

### Post by tonyp1969 on 2008-04-20
That has worked fine. Thank you very much

---

### Post by T-Virus on 2008-04-20
Cheers mate, I'm glad it worked :)

---

