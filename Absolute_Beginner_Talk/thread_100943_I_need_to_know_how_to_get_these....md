---
title: "I need to know how to get these..."
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by SomethingTohide on 2005-12-08
I need the newest java and it's sdk(jre1.5.0_06 and jdk1.5.0_06), and if Ubuntu doesn't already come with it a svn command. Also, as I am VERY new to linux, is there anyway to run commands like

sudo dpkg-reconfigure xserver-xorg
or
$ svn --username anonymous *url*

In the GUI?

Also I need to know howto install these files as I don't know :(

---

### Post by Estariel on 2005-12-08
SUn's java is not open source and therefore a little harder to install than everything else.

Very detailed instructions are here:
[http://ubuntuforums.org/showthread.php?t=76702](http://ubuntuforums.org/showthread.php?t=76702)

Concerning the other questions: Breezy sadly does not contain a graphical tool for configuring the xserver, thus you'll always have to do it from the command line.

About svn: No idea, sorry...

---

### Post by SomethingTohide on 2005-12-08
Nvm about the command line question, I just found out about the terminal :P

Thanks for the link.

---

### Post by steve.horsley on 2005-12-09
Subversion is a package in the normal Ubuntu distro. Slelct System->Administration->Synaptic package manager and then search for subversion. Also notice subversion-tools in the search results. After install, right-click the package and select Properties to see a list of installed files (potential utility program names).

---

### Post by Brunellus on 2005-12-09
1) reconfiguring your xserver is usually not something you do within a running X session.  Most of the time you have to do it, it's because X is broken and you're at a tty console login anyway.

2) For all your java needs, please consult the RestrictedFormats page on the wiki.

---

### Post by SomethingTohide on 2005-12-10
I needed to because I picked the wrong screen resolutions because I thought that was the problem, but it wasn't so I gotta redo that.

---

