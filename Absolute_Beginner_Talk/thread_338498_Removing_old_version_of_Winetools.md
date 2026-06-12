---
title: "Removing old version of Winetools"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-01-14
I have downloaded the most recent winetools =

winetools-o.9jo-III

when I try to install it, it says:

You already installed WineTools. Uninstall the old installation first and come back.

I have tried to use Synaptic, apt-get and aptitude to remove the "old" winetools and nothing is removing it, anybody got another idea?

---

### Post by riven0 on 2007-01-14
You can always manually remove this through the terminal. So fire it up and type:

> cd && ls -a

...to find the winetools directory. Then delete it with:

> rm -r whatever_folder

...and try installing winetools again.

---

### Post by Mark_in_Hollywood on 2007-01-15
> **riven0 said:**
> You can always manually remove this through the terminal. So fire it up and type:

...to find the winetools directory. Then delete it with:

...and try installing winetools again.

I fired up the terminal, but lo! --and behold, there was no folder to be removed (deleted). Is there a winetools "uninstall" within wine itself? 

I'm so confusteded.

Later that day:

In the How-To forum under Wine, I found the solution, success, no more help needed. Thanks.

---

