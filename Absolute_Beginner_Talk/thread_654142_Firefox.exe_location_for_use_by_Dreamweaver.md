---
title: "Firefox.exe location for use by Dreamweaver"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by reklabunde on 2007-12-30
I have installed Dreamweaver under Wine and need to specify Firefox as my browser; however, I have to type in the location of firefox.exe, which I have not been able to find (I thought it might be under /user/bin or /user/lib, but can't find it).   Where is it located on my hard drive?  I'm using Ubuntu 7.10.

---

### Post by icheyne on 2007-12-30
/usr/bin/firefox

To find out, I typed "whereis firefox" into a command line

---

### Post by reklabunde on 2007-12-30
I was able to get Dreamweaver to launch Firefox from that location; however, Firefox would not associate the Dreamweaver file and so the Dreamweaver html did not open in Firefox.  The message I got was: Firefox doesn't know how to open this address, because the protocol (f) isn't associated with any program.  Does this error occur because I'm running Dreamweaver under wine?

---

### Post by jken146 on 2007-12-30
You say you're trying to open a "Dreamweaver file" -- do you mean an html file produced by dreamweaver?  If so, you shouldn't have a problem, as long as you put the correct address into Firefox.  Dreamweaver will be somewhere in ~/.wine/

---

### Post by TeaSwigger on 2007-12-30
Hello, 

WINE unfortunately can't integrate Dreamweaver with the Linux system that tightly. Different protocols etc. But fortunately you still have options:

- A script which will translate commands, allowing you to use a Linux Firefox with Dreamweaver. It's already been written and offered here, I'll look for the link.

- Install Windows Firefox in WINE. 

- Use WINE's own browser, which is built on a Gecko platform, as is Firefox. Characteristics of display should be similar, but I've not tested it.

The third is easiest; simply enter this in a terminal:

```
wine iexplore http://www.google.com
```

and WINE will be prompted to install its browser, which is a very simple and quick process. Dreamweaver can use that.

If you require accurate Firefox rendering for certain, I can only suggest the first two options.

---

### Post by reklabunde on 2007-12-30
From Dreamweaver, one can open a browser from the Dreamweaver toolbar after saving the html file.  This launched Firefox, but Firefox did not open the html that Dreamweaver had saved outside of /wine (in my home directory).  If I went out of Dreamweaver, I can as expected open up the saved file in Firefox - I was hoping to be able to do this from within Dreamweaver like I can do when running Windows.

---

### Post by reklabunde on 2007-12-30
Thank you.  I'll follow up on your suggestions when I have some more time tomorrow.  You have all been a great help.  ~Richard.

---

### Post by TeaSwigger on 2007-12-30
Hello again, I found that thread right away! :)

Howto: Set Konqueror or FireFox Native as default browser for Dreamweaver 8 (wine)
[http://ubuntuforums.org/showthread.php?t=432399](http://ubuntuforums.org/showthread.php?t=432399)

---

### Post by reklabunde on 2007-12-30
You're good.  Thanks!

---

### Post by mick222 on 2007-12-30
> **icheyne said:**
> /usr/bin/firefox

To find out, I typed "whereis firefox" into a command line

Great tip wondered how to find apps ,does it work for anything.

---

### Post by icheyne on 2007-12-31
According to "man whereis", whereis locates the binary, source, and manual page files for a command

:)

---

