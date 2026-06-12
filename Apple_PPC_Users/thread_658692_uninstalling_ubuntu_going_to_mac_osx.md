---
title: "uninstalling ubuntu going to mac osx"
date: 2008-01-04
forum: Apple PPC Users
---

### Post by mattyinthevalley on 2008-01-04
Hey folks. I really love the idea of ubuntu. But it doesnt jive with my skills in computerland. It has not been able to perform to a functional degree for  me. Everything takes me forever to figure out and i dont enjoy trying to figure it out. So I would like to go back to osx.

So I am wondering how I uninstall ubuntu. 

And is there anything I have to do to mac osx installable?

Is ther anyway I can **** my computer up?

Thanks for the help

matty

---

### Post by Vault of Thrones on 2008-01-05
I am pretty sure that if you just wiped your hard drive and installed osx it would be fine.
If you are dual booting then I would think that you could just install osx on a different hard drive partition then go back and erase the first partition.
I don't really know but it seems like it would be pretty straight forward to me.

---

### Post by VidiotGeek on 2008-01-07
If you're at all concerned about preserving your current system install (not having to reinstall all your third party apps, restoring your preferences, restoring emails & other personal data, etc) Then I would suggest using either Carbon Copy Cloner or SuperDuper to clone your Mac OS install to an external FW hard drive first.

After you do that, you can boot from your FW clone & reformat the internal drive as a single HFS+ (Journaled) partition using Disk Utility. You have to do that to wipe out the Linux partitions & reclaim the whole drive for OS X. Once you've done that, just clone your external backup back to your newly (un)partitioned drive & you're good as new!

***EDIT***
I guess I didn't realize from your first post that it seems you are ONLY running Ubuntu right now. I'm dual booting so my directions are really for how to deal with that. If you're going to be starting with a fresh instal of OS X anyway, just boot from a Mac OS install disk & format the entire drive as a single partition HFS+J with disk utility & do a fresh install. Hope this was of some use, unless of course you've already done this a couple days ago.

---

