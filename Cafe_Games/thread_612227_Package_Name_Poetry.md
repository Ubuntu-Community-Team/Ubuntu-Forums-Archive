---
title: "Package Name Poetry"
date: 2007-11-13
forum: Cafe Games
---

### Post by 23meg on 2007-11-13
[Benjamin Mako Hill]("http://mako.cc") had [come up with this idea]("http://mako.cc/fun/package-name-poetry/") quite a while ago: write poetry with Debian/Ubuntu package names only.

You can get the names of all packages in your APT cache with ```
apt-cache search '.*' | perl -p -e 's/^(.*?) -.*$/\1/' | sort
``` or just look around in your package manager. Redirecting the output of the above command to a file may be useful.

If someone can come up with a script that spits out random lines of (semi) meaningful package names (exempting library packages with awkward names, for example), that would be cool. Other interesting things to look into would be [polygen]("apt:polygen") and [dadadodo]("apt:dadadodo") (click to install).

Here's my favorite among Mako's poems:

[QUOTE=Benjamin Mako Hill]
This poem is my political poem. It describes and calls for an anarcho-syndicalist violent uprising against an overzealous United States police-state using only the names of packages in Debian (which is not something, for the record, that I personally advocate):

    The tripwire felt apt-Spy.
    Whois kommander? FBI.

    Meld worker members: Kontact.
    Spread crimson mercury extract.

    Guarddog toppler: Unison!
    Subversion! Flamethrower! Arson!

    Roundup, recover, remind.
    Recite anarchist verse inn rhyme
    Freedroid? Ne! Recode freemind!
    Update freedom inn gnotime.
[/QUOTE]

---

### Post by KIAaze on 2007-11-13
What a crazy idea. ^^
But very creative.

---

### Post by 23meg on 2007-11-13
Indeed; I'm working on my first one.

---

### Post by init1 on 2007-11-13
> **23meg said:**
> [Benjamin Mako Hill]("http://mako.cc") had [come up with this idea]("http://mako.cc/fun/package-name-poetry/") quite a while ago: write poetry with Debian/Ubuntu package names only.

You can get the names of all packages in your APT cache with ```
apt-cache search '.*' | perl -p -e 's/^(.*?) -.*$/\1/' | sort
``` or just look around in your package manager. Redirecting the output of the above command to a file may be useful.

If someone can come up with a script that spits out random lines of (semi) meaningful package names (exempting library packages with awkward names, for example), that would be cool. Other interesting things to look into would be [polygen]("apt:polygen") and [dadadodo]("apt:dadadodo") (click to install).

Here's my favorite among Mako's poems:
Or you could just do this
```

apt-cache pkgnames

```
Cool idea. I'll have to try it.

---

### Post by -grubby on 2007-11-21
I can't think of anything

---

