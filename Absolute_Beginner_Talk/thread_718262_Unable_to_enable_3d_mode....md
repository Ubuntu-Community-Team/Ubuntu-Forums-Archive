---
title: "Unable to enable 3d mode..."
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Laughed on 2008-03-07
Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings.

How do I go about fixing this? 

Noob.

---

### Post by mikeyphi on 2008-03-08
> **Laughed said:**
> Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings.

How do I go about fixing this? 

Noob.

There are various program-specific python bindings available through Synaptic.
Could you be more specific about the error message - which program or setting?

---

### Post by TrashmanL on 2008-03-08
I don't know about him, but I get the exact same error message when trying to run 3-D Chess.

---

### Post by glennric on 2008-03-08
Install the packages "python-opengl" and "python-gtkglext1"

---

### Post by TrashmanL on 2008-03-08
apt-get install python-opengl worked, but 

E: Couldn't find package python-gtkglext1

I went to the sourceforge page for gtkglext1 and downloaded the source code. When I ran ./configure though, it gave me the following:

No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'pango' found
No package 'pangox' found
No package 'gmodule-2.0' found

I know I have GTK+ installed... there is a command line option to specifiy the directory I suppose I could use

I don't know if I have pango installed or not. If I try apt-get install pango I get:

E: Couldn't find pakacage pango

I'm going to keep trying but  I'm not a Linux guru though, so I imagine I'll run into more problems when I try. I'm sure someone on here will see an easier way and I'll keep checking this thread.

---

### Post by glennric on 2008-03-08
You need to make sure you have the gutsy/universe repositories enabled.

---

### Post by TrashmanL on 2008-03-08
I'm using Feisty Fawn... is gtkglext1 only available in Gutsy?

---

### Post by glennric on 2008-03-08
I am not sure if Feisty has it or not.  It may be named something else in Feisty.  The info I gave you was for Gutsy.  You should upgrade.  Feisty isn't an LTS release so there is no reason not to upgrade.

---

### Post by glennric on 2008-03-08
If you really don't want to upgrade and want to compile the source that you said you downloaded, you need to install the devs for all of those packages the configure script complained about.  For instance for gtk+-2.0 you need to install libgtk2.0-dev.  Usually the debian package names start with lib.

---

### Post by TrashmanL on 2008-03-09
*smacks head*

After quite a while of installing this package and that package trying to get the manual install file to install, I found libgtkglext1 in the Synaptic Package Manager!! It seemed every time I did ./configure it named another development package I didn't have!

I guess I wrongly assumed that if it was available in Synaptic that it would be available with apt-get. 

Or did I just not throw the lib in front of it before? 

Grr.... 

Lesson learned: Search synaptic first, before searching the net!

I've put off the upgrade for now, because I know I'll prob have to reinstall a bunch of packages I've already installed. For one, I have Ubuntu/Kubuntu and Xubuntu all in Feisty. Also, I do have some manually installed programs that, unlike tonight, really aren't in the repositories that I would have to reconfigure and remake afterwards. I've heard there have been major issues created by just hitting the upgrade button in Add/Remove Programs, and I really don't want to reformat and reinstall Ubuntu and do it all over, yet.

---

### Post by glennric on 2008-03-09
Synaptic and apt-get are both frontends for apt.  One is GUI and the other is CLI.  So they both have the same packages.

---

### Post by TrashmanL on 2008-03-09
That's what I had thought. It must just be that I forgot to use lib in front for apt-get. 

Strangely, after all this, I still didn't get that 3D chess game to run in 3D. I didn't even want it that much, I just got frustrated 'cause I couldn't get it. :-(. I now had gtkglext1 but I still didn't have the python bindings for it, and the only versions of that I found were for Gutsy or hardy.

But... I just found this bug report that explains it all:

[https://bugs.launchpad.net/baltix/+source/gnome-games/+bug/71593]("https://bugs.launchpad.net/baltix/+source/gnome-games/+bug/71593")

It's about a year old. Nobody's maintaining the python bindings and there isn't an official build for Feisty, but that bug report has a link to a workaround. I used it, and it worked.

I would have to say this thread is solved now.

---

