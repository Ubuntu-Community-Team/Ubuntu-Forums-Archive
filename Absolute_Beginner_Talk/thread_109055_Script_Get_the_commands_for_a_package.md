---
title: "Script: Get the commands for a package"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by cwaldbieser on 2005-12-27
I have seen a lot of people ask how they are supposed to find the commands for a package they installed via synaptic or apt-get if it didn't put an entry in the menu.  People who are more familiar with Ubuntu know that you can just search the various bin folders or the properties dialog in synaptic and figure out the command.  For newer users, it is sometimes a little more difficult to explain what you are looking for.

I cobbled together the following script that will list all the executable files installed by the package given.  If you save this file somewhere in your command PATH and give it executable permissions, it can be a handy way to figure out the name of the command you want if the name isn't one of the usual suspects.

Save as ~/bin/package-commands (for example).
```

#!/bin/bash

#############################################################
# Prints out a list of all the executable files installed for
# the package name given.
#############################################################

dpkg -L "$1" | xargs -n 1 | { while read FNAME; do if [ ! -d "$FNAME" ]; then if [ -x "$FNAME" ]; then echo "$FNAME"; fi; fi; done; }

```

Typical usage would be:
```

$ package-commands speedcrunch
/usr/bin/crunch

```

---

