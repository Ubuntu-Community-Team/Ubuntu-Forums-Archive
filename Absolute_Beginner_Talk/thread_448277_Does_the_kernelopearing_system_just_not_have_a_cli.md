---
title: "Does the kernel/opearing system just not have a clipboard?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by CSMatt on 2007-05-19
Whenever I have copied and pasted stuff, I always seem to need to leave the original material that is to be cut or copied open and running in order for it to be pasted.  The moment I close the process that holds the cut or copied information, I can no longer paste it.  Why is this?  Does GNU/Linux just not reserve a section of memory for cut or copied material and instead just remembers where the material is in existing memory?

---

### Post by jiminycricket on 2007-05-19
GNOME apps do this already, as of GNOME 2.12.

Firefox doesn't do that, due to a bug and not fully implementing freedesktop.org specifications.

You could try installing klipper or glipper.

---

### Post by wormser on 2007-05-19
I tried glipper and it did not work for me.  :(

---

### Post by Pisi-Deff on 2007-05-19
> **wormser said:**
> I tried glipper and it did not work for me.  :(
When you run glipper a icon appears in the notification area, maybe you didn't run it?
I have to run it every time I boot Ubuntu. :/

---

### Post by CSMatt on 2007-05-19
I also just noticed that you only have to highlight material for it to be on the clipboard.  I don't really like this.  What if I intend to paste material repeatedly but in between that process have to highlight some other text for editing or formatting?  I essentially lose that copied data when I highlight the new material.  Or what if I have to highlight something to replace it with pasted material?  Is there any way I can prevent that from happening?

---

### Post by kaamos on 2007-05-19
> **CSMatt said:**
>  The moment I close the process that holds the cut or copied information, I can no longer paste it.  Why is this?

It is a security feature in X. See also [http://www.pixelbeat.org/docs/xclipboard.html](http://www.pixelbeat.org/docs/xclipboard.html)

---

### Post by wormser on 2007-05-19
> **Pisi-Deff said:**
> When you run glipper a icon appears in the notification area, maybe you didn't run it?
I have to run it every time I boot Ubuntu. :/

I installed it again and figured it out.  How can I make it start automatically each time I boot?

Update:

I think I have it set to automatically run each boot.  System> Preferences> Sessions - Clicked new on the Startup Programs tab and entered in the command glipper.  I have not tested it yet.

---

