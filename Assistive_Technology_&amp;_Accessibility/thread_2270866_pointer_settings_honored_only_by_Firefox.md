---
title: "pointer settings honored only by Firefox"
date: 2015-03-26
forum: Assistive Technology &amp; Accessibility
---

### Post by Dreamer Fithp Apprentice on 2015-03-26
3 years ago I posted this thread: [pointer size changes as it moves over screen]("http://ubuntuforums.org/showthread.php?t=1949371")
Although I have a very different setup now, a lean Openbox under 64 bit 14.04 LTS, as opposed the Mate DE in a 32 bit system then, using a rather different and much lighter set of apps with none of the Mate components I was using at the time, this problem is still exactly the same. There is nothing in the description of the problem in  that thread that I'd change to describe the effect now, except the names of the applications, even though I'm now running a very different system. And this has remained  constant through several version changes, several DEs, lots of different software.  The ONLY program in my current system that honors the pointer setting is Firefox. That doesn't include the title bar of a Firefox window, just the body of the window. With Mirage there is a very thin, maybe only a pixel wide, sweetspot at the left edge of the window when it is maximised where the pointer setting is honored. Right now, I'm using "Large Mouse Cursors" but it has been the same with several.

I tried the approach mentiioned here: [Mouse pointer changes size]("http://ubuntuforums.org/showthread.php?t=2235935")
and that incorporates by reference the one here: [Can't Seem to Fully Change Lubuntu Theme]("http://ubuntuforums.org/showthread.php?t=2234783")

So it's still the same thing after 3 years with at least 3 different window managers. Thanks for reading. Any ideas will be appreciated.

---

### Post by Dreamer Fithp Apprentice on 2015-09-26
For the benefit of those who find this because they are researching a similar problem, I've found a 99% fix for this. I won't mark this solved primarily because I think this is not a proper solution but a work-around hack that works most of the time, for now, for my particular setup, and secondarily because I still occasionally see the problem, but rarely now. On the rare occasions I still see it, I suspect the application may have a built-in pointer selection. But this works most of the time:

I edited  /usr/share/icons/default/index.theme to read:
```
[Icon Theme]
Inherits=LargeMouseCursors
```

I don't remember for sure now, but I think I had to manually copy "Large Mouse Cursors" into /user/share/icons. Anyway, that is where it needs to be.

Copied /usr/share/icons/Large Mouse Cursors to /usr/share/icons/LargeMouseCursors so name would conform to pattern of other themes without spaces, underlines, or dashes.

Edited  /usr/share/icons/LargeMouseCursors/index.theme
to change internal theme name and comment.

Selected LargeMouseCursors in lxappearance and rebooted.

---

