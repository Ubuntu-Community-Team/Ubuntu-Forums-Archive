---
title: "Still can't update, Synaptic won't load!"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by macruadhi on 2007-09-10
I have the icon letting me know that I have updates available, But when I attempt to update the system tries to build the dependancy tree, and then shuts down. It seems it is all because xfont-intl-european is broken. I've tried removing it, reinstalling it, all with no success. Now Synaptic won't load any of the packages, period. Before this happened, I couldn't install new packages either.



Thanks,
Eric

---

### Post by por100pre1 on 2007-09-10
First try this:

```
sudo apt-get install -f
```

and let us know what happens then.

---

### Post by macruadhi on 2007-09-10
E: The package xfonts-intl-european needs to be reinstalled, but I can't find an archive for it.

---

### Post by DjBones on 2007-09-11
ok, i was having a similar problem with deluge getting half-installed and then apt giving me smack..
but after scrounging i found the command to set things straight:
```

sudo dpkg --remove --force-remove-reinstreq (whatever program)
```

---

### Post by macruadhi on 2007-09-11
And here's what I get:

eric@eric-laptop:~$ sudo dpkg --remove --force-remove-reinstreq xfonts-intl-european
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 157576 files and directories currently installed.)
Removing xfonts-intl-european ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exit
dpkg: error processing xfonts-intl-european (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xfonts-intl-european


I've tried reinstalling, but it wouldn't let me.

---

### Post by DjBones on 2007-09-11
so i take it that you still can't use synaptic?
well.. its worth another shot, have you tried:
```
dpkg --configure -a
```

---

### Post by macruadhi on 2007-09-12
Nope, update manager just builds the dependancy tree and then just shuts down, thanks anyway.

---

### Post by ukripper on 2007-09-12
Try this thread -
[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

---

