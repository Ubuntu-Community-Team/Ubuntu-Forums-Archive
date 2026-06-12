---
title: "Is there a comprehensive way to backup Ndiswrapper?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-09-11
I like to have Ndiswrapper backed up, in case of doing Reinstalls, so I can get online without having to be connected first with a wired connection.

But the last few times I tried to use my backup, either the dependencies or the Ndiswrapper Utilities seemed to have somehow gotten lost and Ndiswrapper thus failed to install correctly.

I know this was the problem because once I moved my tower to another area of the house and hooked up wired to my router, I ran the Synaptic Package Manager to install Ndiswrapper and everything went smoothly once I did that.

Is there a comprehensive way to backup Ndiswrapper while being sure that I'm also getting the Ndiswrapper Utilities and Dependencies backed up as well? 

Appreciate any help or assistance. I read something from a search about burning a CD from the cache, but I'm not sure how to do that.

Many Thanks, Frank B.

---

### Post by chrome307 on 2007-09-11
Try using AptOnCD  (via Synaptic) and once installed you'll find it in the System menu.

You can create an AptOnCD which will contain all of the DEB files that you have installed and that are cached in your TEMP folder.

When you do this make sure you choose 'METAPACKAGE' as this will include all the dependencies required.

Goodluck :)

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Brightbelt on 2007-09-12
Thanks for the tip!! Sorry I was delayed responding - I got sidetracked. I will definitely try your suggestion...

Many Thanks, Frank B.

---

