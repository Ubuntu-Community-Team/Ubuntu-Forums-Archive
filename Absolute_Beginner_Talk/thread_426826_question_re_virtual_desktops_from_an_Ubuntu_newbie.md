---
title: "question re: virtual desktops from an Ubuntu newbie"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by atmartin50 on 2007-04-28
Hi all,

I've been using Ubuntu for a month now and, despite some mouse problems, am absolutely loving it.

I have a question regarding virtual desktops in Gnome. Being a bit of a neat freak, I like to have similar applications grouped in 4 desktops. For example, email and office apps in one, Firefox in another, music apps in a third, and graphics and/or chat clients in the last. My first introduction to Linux was via a live CD for Mandrake (now Mandriva). I know KDE is a different desktop environment, but I seem to remember it having the ability to customize desktops so that like applications are grouped according to the user's preferences. Very cool!

Is there a way to do this in Feisty, so that an application always loads to the same desktop? I know this seems like an obsessive-compulsive-type question, but I'd love it if there a way to do this.

Thanks a lot in advance!

---

### Post by Happy_Man on 2007-04-28
You are using Ubuntu, with GNOME? Seems you already are familiar with KDE, why don't you just install that?

```
sudo aptitude install kubuntu-desktop
```

EDIT: or you could use yabbadabbadont's suggestion. @yabbadabbadont: does that work on Kubuntu, too?

---

### Post by yabbadabbadont on 2007-04-28
```
/home/daffy $ aptitude show devilspie 
Package: devilspie
State: not installed
Version: 0.20.2-1
Priority: optional
Section: universe/gnome
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 135k
Depends: libc6 (>= 2.5-0ubuntu1), libglib2.0-0 (>= 2.12.9), libgtk2.0-0 (>= 2.10.3), libwnck18 (>= 2.15.90), libx11-6
Description: find windows and perform actions on them
 This tool will find windows as they are created and perform actions on them, such as resizing, moving to another workspace,
 or pinning them to all workspaces.

```
That should enable you to do what you wanted.

---

### Post by atmartin50 on 2007-04-29
Hi Happy_Man and yabbadabbadont:

Thanks for your quick replies and suggestions!

Happy_Man - I will probably just stick with GNOME, as I only spent several days using KDE.

yabbadabbadont - Probably a silly question, but should I just copy and paste the text you included into a Terminal window? If not, how do I use this command/program?

Thanks a lot for your input and help!

---

### Post by imspecial on 2007-04-29
to install that

either search for this in synaptic and install it from there ```
devilspie
```

or do a```

sudo aptitude devilspie
```

---

### Post by yabbadabbadont on 2007-04-29
He means:```
sudo aptitude install devilspie
```
or ```
sudo apt-get install devilspie
```
or just install it through Synaptic like he suggested.

:D

---

### Post by atmartin50 on 2007-04-29
Thanks imspecial and yabbadabbadont!

I'll do this and report back soon....I appreciate the help!

---

### Post by atmartin50 on 2007-04-29
Hey Guys,

I successfully installed devilspie using the Terminal, then ran it via the command line, but got no response. Any ideas?

Thanks a lot!

---

### Post by yabbadabbadont on 2007-04-29
[http://ubuntuforums.org/showthread.php?t=98071](http://ubuntuforums.org/showthread.php?t=98071)
[http://ubuntuforums.org/showthread.php?t=75749](http://ubuntuforums.org/showthread.php?t=75749)
[http://wiki.foosel.net/linux/devilspie](http://wiki.foosel.net/linux/devilspie)
[http://xlife.zuavra.net/index.php/48/](http://xlife.zuavra.net/index.php/48/)

And there should also be documentation for it in /usr/share/doc/devilspie-XXXXX  (I'm not sure of the exact directory name, but it will start with devilspie)  There should be a README (or similar) file there as mentioned in the first link I provided.

---

### Post by atmartin50 on 2007-04-30
Thanks for the input folks....

However, in the interest of time, I have decided that switching over to KDE would be a bit easier than using Devil's Pie in GNOME. After a month of using GNOME, it's taken me a while to get used to KDE, but I think I really like it, overall.

Which brings me back to my original issue---could anyone tell me how to configure virtual desktops so that the same applications always load in their assigned work space? 

Thanks a lot in advance!

---

### Post by atmartin50 on 2007-05-01
Hi folks,

Please disregard my last post, as I answered my own question, but only just before I decided to switch back to GNOME. KDE is nice, but it just seemed too cluttered and it also seemed to slow my system down. GNOME all of a sudden seems very elegant in its simplicity and ease of use.

---

