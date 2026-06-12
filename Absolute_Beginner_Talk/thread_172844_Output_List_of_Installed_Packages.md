---
title: "Output List of Installed Packages"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Charlatat on 2006-05-09
Any way to get a list of installed packages on a system?  Would help to generate it from an existing machine and use it as a reference when formatting/reinstalling...

---

### Post by Azrael on 2006-05-09
dpkg -l

---

### Post by christhemonkey on 2006-05-09
(I think Azraels method is better)

```
sudo apt-cache -n >> ~/installedpackages.log
```

Something like that anyway.

That will work as long as you havent cleared your cache, or downloaded packages with synaptic, but then chosen to not install them.

---

### Post by halfvolle melk on 2006-05-09
Check out the post by Azz. Maybe that's what you're looking for.
[http://ubuntuforums.org/showthread.php?t=169062](http://ubuntuforums.org/showthread.php?t=169062)

---

### Post by christhemonkey on 2006-05-09
That would only give you the packages that you have selected to be installed, as opposed to the ones already installed, i think anyway.

---

### Post by rdd on 2006-05-09
check out this one too.

[http://www.linuxforums.org/forum/debian-linux-help/40955-need-list-installed-packages.html]("http://www.linuxforums.org/forum/debian-linux-help/40955-need-list-installed-packages.html")

---

### Post by halfvolle melk on 2006-05-09
[QUOTE=christhemonkey]That would only give you the packages that you have selected to be installed, as opposed to the ones already installed, i think anyway.[/QUOTE]
You made me want to test it ;) It works for me after replacing
```
cat file > dpkg --set-selections
```
with
```
cat file | sudo dpkg --set-selections
```

---

### Post by scooper on 2006-05-09
It's one of the few unpleasant surpises for me with a Debian-based system, that this simple need isn't more obviously solved.

FWIW I usually tweak the command to be:

```
dpkg -l | grep ii
```

This limits it to packages that are completely installed.

---

### Post by christhemonkey on 2006-05-09
Haha fairy snuff  halfvolle melk!

on rpm based distros you can just do ```
rpm -qa
```
But as for debian based distros....lol.

---

### Post by Azrael on 2006-05-09
I see a lot of redundancy here...
[quote=christhemonkey]on rpm based distros you can just do ```
rpm -qa
``` But as for debian based distros....lol.[/quote]
How is *dpkg -l* less simple than *rpm -qa*? :-k

---

