---
title: "Installing Programs..."
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by -=Raven=- on 2006-03-15
I know people are probably avoiding me like the plauqe but ive got a problem. Ive just download Frostwire and i havent got a clue how to install it or any other program for that matter.

Ive unzipped it and put it in my home directory in a folder called frostwire and now im stuck. I have looked all over this forum and on various other sites before i thought i should ask for help.

Cheers

---

### Post by mlind on 2006-03-15
you've got at least two choices.

You can download Frostwire Debian/Ubuntu binary from the Frostwire's site
and install the package with command
```

sudo dpkg -i FrostWire-4.10.9-1.i586.deb

```

just make sure package name is the same you downloaded.

other option is to download gzipped tarball or zip package, create directory
somewhere below your home folder, extract the contents there and run program locally.

---

### Post by -=Raven=- on 2006-03-15
Do i have to do that command with every program i download?

---

### Post by aysiu on 2006-03-15
Here's a general guide:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If you downloaded to your desktop, make sure to ```
cd Desktop
``` before running mlind's command.

---

### Post by aysiu on 2006-03-15
[QUOTE=-=Raven=-]Do i have to do that command with every program i download?[/QUOTE] Most programs you can download *and* install with a single command. In fact, with one command, you can download and install numerous programs at once.

For more info, see the link I posted above.

---

### Post by -=Raven=- on 2006-03-15
Thank you :-D

---

### Post by mlind on 2006-03-15
[QUOTE=-=Raven=-]Do i have to do that command with every program i download?[/QUOTE]

That dpkg command is used to install .deb packages you've downloaded from internet.
There are several ways you can install software on Ubuntu distro, but .deb packages
are the easiest to install, uninstall and otherwise manage.

I suggest you get familiar Synaptic and apt-get (command-line)
tools that are especially for installing software without too much hassle.

see [this]("https://wiki.ubuntu.com/UserDocumentation#head-57224fc8a4bfcbe0286245ae95b4f4c7ebb4c4ef") wiki thread

---

