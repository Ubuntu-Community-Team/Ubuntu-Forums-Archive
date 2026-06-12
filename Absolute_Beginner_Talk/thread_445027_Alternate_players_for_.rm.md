---
title: "Alternate players for .rm"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Dev'olution on 2007-05-15
Hey Guys,

Are there alternate programs to open .rm files... I have struggled to find one :(

Thanks,
Kris

---

### Post by Happy_Man on 2007-05-15
i'm reasonably sure there is a version of RealPlayer 10 in the repos... have you searched?

---

### Post by bukwirm on 2007-05-15
Xine with the extracodecs packages installed works for me.

---

### Post by Dev'olution on 2007-05-15
Oops forgot to add i'm using a UWA repository and hence there is no realplayer there :(

Are there any other programs on ubuntu that can open .rm files?

---

### Post by starcraft.man on 2007-05-15
Hmmm, I'm not sure if its in the repos, I know there is a bug with the last version I installed and its only recently been fixed for feisty.

To install from the new build is simple.
[URL="http://forms.helixcommunity.org/helix/builds/index.html?filename=20070515/player_all-realplay_gtk_current-20070515-linux-2.2-libc6-gcc32-i586@rhel4/RealPlayer-10.1.0.3147-20070515.i586.rpm"]
Download this[/URL].

Open a terminal (applications > accessories > terminal) and type in: 
```

sudo aptitude install alien
```

Then, convert it to debian with [Ubuntuguide.]("sudo alien -d package_file.rpm")

Bacially just use this command and replace /path with the path to the file, whether its desktop or home folder wherever you downloaded it.

```
sudo alien -d /path
```

Thats it, then just install the debian.

You need this latest build too, apparently there was an issue when playing certain RM files with the old version. That should be it.

---

### Post by Dev'olution on 2007-05-15
Downloaded,converted and installed the RPM but it hasnt installed Realplayer :S

Where is it located once installed?

---

### Post by ugm6hr on 2007-05-15
I couldn't find Realplayer 10 in the Ubuntu repos - but it is available as a Debian package:
[http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb](http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb)

Just open it with GDebi (double click it from file manager - or open it directly from Firefox).  It should then just work (mine did - installed earlier today).  It should also be relatively easy to uninstall later if necessary.

---

