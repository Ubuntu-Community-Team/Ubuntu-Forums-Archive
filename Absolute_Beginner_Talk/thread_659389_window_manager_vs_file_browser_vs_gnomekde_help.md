---
title: "window manager vs file browser vs gnome/kde help"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by 4m3n on 2008-01-05
This isn't so much a direct question as it is a cry for clarification and understanding.

What I am trying to do is understand the roles played by and relationships between the components of the operating system which govern the user interface.

Basic Info:  I run Ubuntu 7.10 (gutsy gibbon) with almost entirely default settings but some additional packages, mainly for audio and video files with corresponding codecs and firefox plugins.

I began to wonder about this topic when a friend who used to run fedora and does some linux work at school had me install the no-longer-supported ion3 package, which I suppose is a window manager?  

1. What is a window manager?  (and don't just say a program to manage the windows)  What are some of the better known window managers out there?

Did ion3 temporarily replace nautilus (a file manager?) or gnome?  How come ubuntu can run both gnome and KDE applications?  Where does nautilus fit in?  How does all this work?  Basically what I am asking for is an explanation and a system of taxonomy for the following packages:

gnome/kde
nautilus/x11/ion3
compiz/beryl/emerald
qt/konqueror

How do these (and I'm sure many many other programs in the same vein) fit together?  Which ones can coexist and how do they interact?  I need a general, basic response detailing the framework these all fit into.  Thanks in advance for any efforts to help me figure this out.  I will be doing my own reading and would be grateful if you posted a link to an explanation given somewhere, provided I can understand it and it answers my questions.

Thanks again.

---

### Post by 4m3n on 2008-01-05
Additionally, if anyone can point me in the right direction to learn in general how ubuntu is put together and how it works, rather than just user directed how-to-get-it-to-do-what-I-want stuff like the documentation site I would like that too.

---

### Post by LaRoza on 2008-01-05
It controls how the windows are drawn, Fluxbox and Metacity are Window Managers.

The GTK and QT libraries (which are used by GNOME and KDE respectively) are used by applications but are not part of them. To use a KDE app, you need the required libraries. GNOME doesn't come with them, but you can install them. The libraries are not loaded when GNOME is, so a KDE apps takes a second to start but runs fine.

gnome/kde
nautilus/x11/ion3
compiz/beryl/emerald
qt/konqueror

GNOME and KDE are Desktop Environments, you can install more than one on the same system

Nautilus is a file manager, X11 provides the basis for GUI's.

Compiz is a project that does all the fancy desktop effects, Beryl was a fork of the original Compiz project and is no longer being worked on, Compiz-Fusion is the new thing. 

QT is a library to make GUI's, KDE uses it. Konqueror is a file manager/browser/control panel in KDE.

---

### Post by aun on 2008-01-05
Gnome and KDE are (the two primary) desktop environments.  If you are running default Ubuntu you are using Gnome.  Window managers are the software that handles window placement and rendering on the desktop (I think).  File browsers are software that let you navigate around your filesystem.  They are often also web browsers.  Konqueror is both a Web browser and file browser, and is the KDE version.

Both desktop environments have many other applications written to be compatible with them, and bundled with them to some degree or another.  KDE apps often start with "K", and Gnome with "G".

In the Microsoft word the OS and desktop environment are both referred to as Windows.  Windows Explorer is the file manager/browser (well, used to be - I'm not sure now).  Internet Explorer is the web browser.  (These are really the same).

The X Window system is the software that actually handles rendering all windowed graphics, and is used by both desktop environments. (Way simplified)

---

### Post by 4m3n on 2008-01-05
Thanks folks.  I didn't quite get the general understanding I was looking for, but your comments helped.

---

