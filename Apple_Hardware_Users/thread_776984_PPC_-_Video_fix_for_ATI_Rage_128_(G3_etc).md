---
title: "PPC - Video fix for ATI Rage 128 (G3 etc)"
date: 2008-05-01
forum: Apple Hardware Users
---

### Post by stream303 on 2008-05-01
While researching some Hardy video problems, I can't believe I forgot about these details for G3's although I think it will also apply to any box running an ATI Rage 128:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

(Sure wish this was a sticky!)

I was hunting around and saw that ATI Rage 128 cards hang on glx, among other things:
[http://gentoo-wiki.com/HOWTO_AIGLX](http://gentoo-wiki.com/HOWTO_AIGLX)
and then I remembered that wiki listed above.

So for anyone running ATI Rage 128 cards, the wiki will be extremely helpful.  Unless you are running a G3 iMac, your resolutions may be a bit different.

A working xorg.conf can be seen here, filled in with a bit more user-added detail:
[http://ubuntuforums.org/showthread.php?p=4808544](http://ubuntuforums.org/showthread.php?p=4808544)

Hopefully by disabling the glx and dri modules, possibly adding -nosplash- to your kernel parameters at either the second stage boot prompt, and maybe having to tweak your horizontal and vertical resolutions, you'll have some nice video. :)  it can be done!

---

