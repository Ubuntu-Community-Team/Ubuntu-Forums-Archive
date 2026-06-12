---
title: "Need guide to dwnld &amp; install GoogleEarthLinux"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2006-10-04
Would someone steer me to a guide to download and install Google Earth. I tried on my own and had it would never work, so I deleated all the googleearth files and want to start clean.

---

### Post by SoggyCornflake on 2006-10-04
Check out Automatix (not sure if that's spelled correctly).  It's a tool for easily configuring Ubuntu, and it includes GoogleEarthLinux.

Do a seach around here for Automatix and have fun.:D

---

### Post by kindafunnylookin on 2006-10-04
Will do,
Thanx

---

### Post by aysiu on 2006-10-05
If you want just Google Earth, [here's a script](http://www.ubuntuforums.org/showpost.php?p=1138374&postcount=24) that will do it for you.

If you have a bunch of stuff you want installed for you, Automatix is the way to go.

---

### Post by kindafunnylookin on 2006-10-05
I ended up installing Automatrix and using it to install GE. However after it installed and I ran the program it loaded then connected to the server, then started loading something else and just flicked off. This happened repeatedly.
Should I now try the way u suggested?
Peter

---

### Post by aysiu on 2006-10-05
I'm not really sure how Automatix installs Google Earth, so I think it's worth a shot.

---

### Post by kindafunnylookin on 2006-10-05
Hi
I gave it a try and this is the result:

peter@ubuntu:~$ chmod +x installge
peter@ubuntu:~$ ./installge
--22:13:42--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 64.233.179.91, 64.233.179.93, 64.233.179.95
Connecting to dl.google.com|64.233.179.91|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.2091..................................................................
Installing mimetypes...
Running /usr/bin/update-mime-database /home/peter/.local/share/mime
***
* Updating MIME database in /home/peter/.local/share/mime...
Wrote 2 strings at 20 - 6c
Wrote aliases at 6c - 70
Wrote parents at 70 - 74
Wrote literal globs at 74 - 78
Wrote suffix globs at 78 - d0
Wrote full globs at d0 - d4
Wrote magic at d4 - e0
Wrote namespace list at e0 - e4
***
Installing desktop menu entries...
Error: Rage 128 timed out... exiting
Password:
peter@ubuntu:~$


Most of that means nothing to me, Where to go from here?
Thanks for putting that script together.

---

### Post by aysiu on 2006-10-05
Hm.

I've never seen that error before, but I Googled it. Apparently, you're not alone:
[http://www.suseforums.net/index.php?showtopic=24718](http://www.suseforums.net/index.php?showtopic=24718)
[http://bbs.keyhole.com/ubb/showthreaded.php?Number=446778](http://bbs.keyhole.com/ubb/showthreaded.php?Number=446778)

Unfortunately, neither link contains a solution. I'll keep looking...

---

### Post by kindafunnylookin on 2006-10-05
Thanks, I'll check back in the morning.
Peter

---

