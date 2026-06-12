---
title: "again realplayer"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Bahal on 2006-09-24
I still have problem with installing the realpalyer.
what I've done so long:
-    From Ubuntu dapper, I tried to run the link "sudo apt-get install realplay". But I got this message:
                                 Reading package lists... Done
                                 Building dependency tree... Done
                                 E: Couldn't find package realplay
-    Then I updated my repositories which helped me to bring the "realplayer v.8" to my "Not installed"-list in Synaptic Package Manager

-    So I tried to mark it for installation, but I got this message:
                                 Depends: xlibs  but it is not installable
-    I checked my installed-list and found out that I already had "xlibs-dev"

-    I tried the same thing from <Applications/Add-Remove> with no result.

-    Running the Automatix from System Tools didn't help either, even though I checked the "realplayer" in the source list to be installed.

I'll be happy if any one could help me...because I need realplayer to see some lectures on my pc with the format <.rm>  [-o<

---

### Post by petit.padavoine on 2006-09-24
```
apt-get
``` will only work for packages which are part of the default repositories. RealPlayer is not...
To install:

[LIST=1]
[*]Point your browser to [The RealPlayer for Linux website]("http://www.real.com/linux")
[*]Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.
[*]Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.
[/LIST]

There you go!

P.S. This applies to all programs, because not all are available as .deb packages. If you're looking for a program, search for it in Synaptic or in the Ubuntu package search, and if you can't find it, do a Google search for it.

---

