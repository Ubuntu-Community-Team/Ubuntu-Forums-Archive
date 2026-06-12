---
title: "KXDocker does not save adjustments"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by ubuntrix on 2006-10-29
Hi there,
I bet there will be an easy answer ;) but I am lost at the moment...

When I change the number of icons and layout of icons in/with KXDocker, it seems as they are not saved (and yes, I clicked appy and save several times).
When I log out and back on again, some icons are missing, others are added.

Any idea?
Many thanks in advance,
Ubuntrix

---

### Post by wieman01 on 2006-10-29
Have you installed the version that is in the repositories (0.39 or something)? Honestly I would download the latest one & compile it from scratch. If you need help compiling it, no problem, but I'd rather drop this version because it's really not up to standard anymore. 

You find the latest version here: [http://www.kde-look.org/content/show.php?content=10955]("http://www.kde-look.org/content/show.php?content=10955")

The developers have added a number of great features recently. Full transparency support, alignment on top, etc. So you may give it a go...

Drop us a line if you need a hand when compiling it. Can be quite a b@#$!

---

### Post by wieman01 on 2006-10-29
BTW: The reason why changes you have made won't stick is because KXDocker's configuration file is somewhere in "/usr/local..." or similar. The permission as set in such a way that the file belongs to root (= the admininstrator in Windows terms), so your local user who runs KXDocker won't be able to change it.

The new version of KXDocker store the configuration file in the home-folder:
[QUOTE/home/[COLOR="Red"]your_user[/COLOR]/.kde/share/apps/kxdocker][/QUOTE]
This way your normal user can change the config-file with no problem. The ffile belongs to you.

I recommend to get the latest version of KXDocker... Way better.

---

