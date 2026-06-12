---
title: "Can't install software"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by pleasedontspamme on 2006-12-29
I am new linux in general, but have been trying ubuntu for a week now, and I want to add some software that isn't in any pakage I can find. It is the game warzone 2100. I downloaded it for scource forge, and unpakaged it, but I can't get it to install. It has something called install-sh, but when I run it, nothing happens. Can anyone help me.

---

### Post by pseudonym on 2006-12-29
> **pleasedontspamme said:**
> I am new linux in general, but have been trying ubuntu for a week now, and I want to add some software that isn't in any pakage I can find. It is the game warzone 2100. I downloaded it for scource forge, and unpakaged it, but I can't get it to install. It has something called install-sh, but when I run it, nothing happens. Can anyone help me.
[This thread]("http://www.ubuntuforums.org/showthread.php?t=282219&highlight=warzone+2100") has some links which will help you. FYI, I found it in the [Ubuntu Gaming Forum]("http://www.ubuntuforums.org/forumdisplay.php?f=93"). :)

---

### Post by steve.horsley on 2006-12-29
Open a command prompt (terminal) window and change to the directory where install-sh is, e.g.
**cd warzone2100**

install-sh is almost certainly an installer script. You must first make it executable with this command:
**chmod +x install-sh**

You may be able to run it with this command:
**./install-sh**
but it will fail if it wants to write to folders outside of your home directory. To give it permission to write to files anywhere, use this command:
**sudo ./install-sh**

If it prints any error messages, post them here for more help.

---

### Post by illu45 on 2006-12-29
There are some pretty good instructions on [this thread]("http://www.ubuntuforums.org/showthread.php?t=321523&highlight=tar%2Cgz"). 

Generally speaking, though, start off by opening a Terminal and going to the directory where you unpacked the file. Type ./configure and press enter. If there are no errors, type "make" and press enter, then "make install" and "make clean", as macogw says.

---

### Post by pleasedontspamme on 2006-12-29
when I enter ./configure I end with this error.
checking for SDL - version >= 1.1.4... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: You need to install SDL ([http://www.libsdl.org/)](http://www.libsdl.org/)).

When I check Synaptic, it says I have SDL Installed

---

### Post by pseudonym on 2006-12-29
Ignore my post: Entered by mistake. My apologies.

---

### Post by pleasedontspamme on 2006-12-29
I found where i set the variable, but I don't know what to set it to. I can't find anything that is called SLD-Config. where would that be?

---

### Post by Perfect Storm on 2006-12-29
Ubuntu Gamers Arena Howto on Warzone 2100 - [http://gaming.gwos.org/index.php?option=com_content&task=view&id=82&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=82&Itemid=63)

---

### Post by Ptero-4 on 2006-12-29
you need the -dev packages for SDL.

---

