---
title: "Uninstalling Ubuntu Apps"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-04-21
I would like to uninstall Evolution and Ekiga and some other apps from Syanptic however it says it will also remove ubuntu-desktop if I uninstall these files. How can I remove these software without uninstalling my desktop?

---

### Post by GSF1200S on 2007-04-21
> **syalam said:**
> I would like to uninstall Evolution and Ekiga and some other apps from Syanptic however it says it will also remove ubuntu-desktop if I uninstall these files. How can I remove these software without uninstalling my desktop?

I dont know exactly why its doing that.. maybe somebody else can chime in on this...

Have you tried using Add/Remove Programs in Applications>Add/Remove Programs?

You should be able to either search for the programs you want to uninstall, or just manually browse for them by category.

---

### Post by Tundro Walker on 2007-04-21
Heh, this was one of the first things I learned after installing Ubuntu, because I, too, wanted to get rid of some apps I didn't use.

Ok, for starters, the "ubuntu-desktop", along with "kubuntu-desktop" and "xubuntu-desktop" are just "meta" packages, meaning they aren't real applications, they're mostly just dependency lists tying various things together to for the "?buntu-desktop".

You can select the "ubuntu-desktop" for removal, and click "Apply" to get rid of it.  This will break the dependancy chain, letting you select and uninstall other programs.

I also recommend checking out WackToMack's ["How To" post about Clean Up.]("http://ubuntuforums.org/showthread.php?t=140920&highlight=clutter+control")
Once you remove a lot of things, there may be some config files left over if you didn't do "full removal".  And, there may be leftover libraries and such that are no longer needed if they are dependancies of anything left on your machine.  So, using apt-get and deborphan (or an orphan filter in Synpatic), you can find them and bump them off.

After all the removal and cleaning, I got my Ubuntu install down to about 1gb...to which I then bloated it back up with about 2-3gb worth of mp3's, games, and IDE's...LOL!

---

### Post by olavjunior on 2007-04-23
Thanx! Very informative :)

---

