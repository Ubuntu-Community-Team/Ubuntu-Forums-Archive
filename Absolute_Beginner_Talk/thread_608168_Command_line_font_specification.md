---
title: "Command line font specification"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by cknight on 2007-11-09
Anyone know where I can find the syntax for specifying fonts on the command line? E.g. here's the excerpt from the man page:
```
       -f font
              Set font (Default: -*-lucidatypewriter-bold-*-*-*-*-240-*-*-*-*-*-*)

```

but I have no idea what all the fields are. 

Thanks!

---

### Post by llamakc on 2007-11-09
Do you mean in Gnome-Terminal, Xterm, the console, or what?

---

### Post by cknight on 2007-11-09
Not sure what you mean.  Specifically,I'm trying to set the font for the 'osdsh' program to be executed from a bash shell.  The man page for this program shows the default font used and I presume that all the '*' between the dashs are configurable, but I can't find any documentation on what all the bits mean.

---

### Post by llamakc on 2007-11-09
Can't you set the font is osdshconfig?

---

### Post by cknight on 2007-11-10
Yes, osdshconfig allows you to set the font.  Its default value is 'fixed'.  Not sure what that means and the only other value that seems to work is the default string in the man page (e.g. -*-lucidatypewriter-bold-*-*-*-*-240-*-*-*-*-*-*).  Do you know how to choose a different font using osdshconfig?  Thanks.

---

