---
title: "Uninstalling Printer Drivers (Maybe)"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by 42Wired on 2007-02-14
I have been trying to install my Canon Pixma MP500 using some of the methods in [this]("http://ubuntuforums.org/showthread.php?t=198731") thread.

If I want to try something else, will I have to uninstall the other drivers I've installed? If so, how would I go about doing that? Also, I haven't tried it yet, but would installing multiple drivers hurt anything?

So far, I've tried TurboPrint (which almost works) for printing functionality, and [this]("http://home.arcor.de/wittawat/pixma/") site's drivers for scanning functionality.

---

### Post by mssever on 2007-02-14
You shouldn't have to uninstall the drivers. But I don't know for certain.

If you want to uninstall them, use Synaptic to remove them. I noticed that the thread referenced an RPM (I only read the first post). If you converted an RPM using alien, you can still uninstall it through Synaptic. If you installed from source or via some non-standard installer, then you'll have to check the documentation.

---

### Post by 42Wired on 2007-02-14
I didn't have to convert anything; I only downloaded deb files.

Alien sounds like a useful tool. Is it just used for converting file types, or does it perform other functions, as well?

Also, how would I go about accessing it?

---

### Post by mssever on 2007-02-14
Deb files are easy to uninstall. Just use synaptic or aptitude to remove them. See the links below for more.

Alien is useful for converting between package formats (different distributions use different native package formats), but it's best to stick with .deb files whenever possible as they're Ubuntu's native format. When you use alien to convert RPMs, you don't get any dependency checks, so that you could end up missing some important files and end up with it not working.

Also, it's best to use .debs built for the version of Ubuntu you're using, not a different version or a different distro (Debian, Mepis, etc.) in order to avoid dependency problems.

Synaptic is a graphical package manager that many people find easier to use than the command line tools apt-get and aptitude. They all do basically the same, though.

Here are a couple of good guides for installing software in Ubuntu:
[LIST]
[*][http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[*][http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)[/LIST]

---

