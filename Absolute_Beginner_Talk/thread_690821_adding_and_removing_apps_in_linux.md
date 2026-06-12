---
title: "adding and removing apps in linux"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by tone33 on 2008-02-07
So coming from Windows I'm inherently cautious against installing several different applications because of the footprint they often leave behind after "removing" them through XP or Vista remove features.  Does this problem also exist in Ubuntu?  I would think that the fact that Linux uses text files in lieu of a registry is a step in the right direction to solve this problem...

---

### Post by Haluci on 2008-02-07
As a fellow former Windows user, I've never had a problem with it myself.  Just uninstall your applications through Synaptic Package Manager and you should be fine.

---

### Post by Rocket2DMn on 2008-02-07
Programs sometimes leave configuration directories in your home folder or an Applications menu entry.  These can be removed manually, but there is also a nice guide here to remove extra stuff that gets left behind over time:
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)
and
[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

---

### Post by gavintlgold on 2008-02-07
Yes, Ubuntu does clean out most files. If you want to completely remove the extra settings files (which are usually very small text files) you can run "sudo apt-get --purge remove" in the command line, or use Synaptic Package Manager and mark the app for "Complete Removal".

However, if you install files using other methods like compiling, none of this is certain (since it depends on the makefiles, AFAIK). Of course, most of the time users won't do this so that's not important.

You aren't going to get the same types of clogging that windows has, although some cached package files might remain in the system, cleanable with "sudo apt-get clean".

You don't have to do that though unless you have <100 MB free on your hard disk :D

Also, since most packages use shared libraries, they are generally smaller than with windows. I think that helps make everything more compact. I have not a problem with uninstalled programs' footprints.

---

### Post by drs305 on 2008-02-07
It is not a problem in ubuntu using synaptic. Linux does a great job of keeping things relatively straight. I install and uninstall lots of programs, including many that perform the same function. I can't remember the last time I had a problem doing this. 

And remember, synaptic has various options when you uninstall, including removing the used files or deleting the entire archive. You can also see exactly what files you are about to uninstall by selecting the app and then clicking on the Properties box at the top. That is not really necessary but you can look at them if you are the nervous type :(

---

### Post by tone33 on 2008-02-07
ok, thanks for all the replies!

---

