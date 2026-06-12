---
title: "probably a very stupid question..."
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by bartfliet on 2007-10-04
When looking for tutorials on how to install some application, I have seen this a couple of times 

```
/etc/apt/sources.list
```

What does this mean? and where do you have to input that?

---

### Post by misfitpierce on 2007-10-04
It means you open a terminal and type sudo gedit /etc/apt/sources.list

then list of repo's will show and at bottom you enter the line it says to add. This ensures the program is always up to date.

No such thing as a dumb question... Just a dumb answer

---

### Post by forestpixie on 2007-10-04
it's the list that Ubuntu, or whichever flavour your using, uses to get it's downloads from - basically a list of web addresses

if you need to edit it for any reason you use gedit (for Ubuntu) like this in a terminal

```
gksudo gedit /etc/apt/sources.list
```

try to use [gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo") instead of sudo when your using a graphical application 

hope that helps

---

### Post by hyper_ch on 2007-10-04
Most software on Linux is contained precompiled (sort of like .exe files) in centralised places called "repositories".
That file, the sources.list, contains a list of repositories for wich programs like apt-get, aptitude, synaptic, adept etc. will look for available software. You have a default set of trusted repositories and you can add your own to it.

This website [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) can create a sources.list with the most common/popular trusted repositories. The medibuntu one, for example, has codecs to read encrypted dvds and to play all kinds of music/video files. The canoncial one features for example Skype...

---

### Post by bartfliet on 2007-10-04
Thanks alot youz guys!

---

### Post by Rui Pais on 2007-10-04
Another way to edit that list using a GUI is synaptic.
On menus go Settings -> Repositories. You can there turn them on/off, edit, add and delete.

Sometimes it's safer for new users :)

---

### Post by justinmiller87 on 2007-10-04
> **hyper_ch said:**
> Most software on Linux is contained precompiled (sort of like .exe files) in centralised places called "repositories".
That file, the sources.list, contains a list of repositories for wich programs like apt-get, aptitude, synaptic, adept etc. will look for available software. You have a default set of trusted repositories and you can add your own to it.

This website [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) can create a sources.list with the most common/popular trusted repositories. The medibuntu one, for example, has codecs to read encrypted dvds and to play all kinds of music/video files. The canoncial one features for example Skype...
Excellent link. I can't wait to use it when I build my new system.

---

