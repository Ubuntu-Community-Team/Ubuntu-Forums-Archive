---
title: "Secure Delete"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-02
After reading the documentation for Secure-Delete from THC, I determined that it would be difficult and too dangerous for a newbie like me to use. From what I gathered, it's function commands, if you don't know what you are doing, ( and I don't)  can cause a lot of damage to your system. Is there a secure delete program with a Gui for Ubuntu, or one that attaches itself to gnome, kind of like Bcwipe does with windows explorer? Don't get me wrong, I like the command line, but in this case, right now, i think I would regret it....

---

### Post by georider on 2007-12-28
Kgpg offers a shredder that will allow you to drag and drop files onto it. It overwrites the files several times. The trick is that files can be caught in your print spooler or in backup files such as Vim creates. So you would simply need to be aware of any copies that might be on your system.

Once kgpg is installed, you simply install the shredder by running kgpg and opening the settings dialogue. Then choosing the Misc tab at the bottom.

Sorry, I'm not familiar with the other applications you had mentioned so I cannot compare them to what kgpg offers.

HTH

-g

---

### Post by mc4man on 2007-12-29
[http://ubuntuforums.org/showthread.php?t=531703&highlight=shred](http://ubuntuforums.org/showthread.php?t=531703&highlight=shred)
very simple to set up, gives you a right click option to shred and delete files, can also be used on folders to shred what's in them - won't shred/delete folders (directories) themselves

i used this as a parameter - the reason escapes me at the moment
```
%M -type f -exec shred -v -u  '{}' \; 
```

---

