---
title: "Upgrade stalled"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by 1972_OLDS_442 on 2007-05-04
Hello I just started my first update for Edgy and ran into a problem. It downloaded and installed the  about 3/4 ths of the downloads fine then it got to "Configuring capplets-data" and has stalled for about 20-25 minutes, the detail box dropped down by itself as if I am suppose to input a command.


How do I tell it skip it or get it to continue installing the rest of the downloads?

---

### Post by teddybairs1 on 2007-05-04
Dude, I wish I could tell you. The same thing happened to me when I tried to upgrade from edgy to feisty. It froze my system and I tried, like an idiot, to shut it down and restart. I lost my system and had to do a clean install from a burned disk.

If I might make a suggestion, try shutting down the upgrade manager and restarting it. It might work to finish configuring it.

If all the packages are already downloaded you can try running

sudo dpkg --configure-any

in a terminal/konsole. This will tell it to set up the rest of the packages which haven't been configured yet, assuming they've all been unpacked.

check the --help feature on dpkg for all of the commands. It's changed over the years a little and I don't remember all of the proper syntax for the current version in Ubuntu.

Don't know if this will work at all, but it's worth a shot. The alternative is "trash & burn" your system and start fresh with a newly burned Feisty disk.

---

### Post by 1972_OLDS_442 on 2007-05-04
tried to close the update manager, and it won't close.:( 

thanks for idea though

---

### Post by 1972_OLDS_442 on 2007-05-04
Never mind the d*** thing decided to start working for no reason after doing nothing for 45 min.

Thanks again:mad:  for the info

---

