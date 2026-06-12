---
title: "Cannot get Firefox to run"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by TennSeven on 2007-01-23
Ok, so I installed Firefox using the guide (basically just downloaded the tar.gz from Firefox website and extracted it to /opt/firefox).  When I run /opt/firefox/firefox nothing happens, the terminal just goes to the next line basically acknowledging that I entered a command but nothing happens after that (no Firefox window, no message, nothing).  If I try to run /opt/firefox/firefox-bin I get the message "error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory".  I'm pretty sure I need to run firefox and not firefox-bin, but why can't I get it to do anything?

TIA

TennSeven

UPDATE: Just before I posted this I tried sudo /opt/firefox/firefox and it came up! Is there some reason I have to sudo? Can I set it up so anyone can run it?

---

### Post by teitunge on 2007-01-23
what happens if you just write firefox in your terminal? or choose it from the menu?

---

### Post by crossedout on 2007-01-24
Read through [[COLOR="Blue"]this[/COLOR]]("https://help.ubuntu.com/community/FirefoxNewVersion").
It sounds like maybe you missed a step.

-Xout

---

### Post by TennSeven on 2007-01-24
> **crossedout said:**
> Read through [[COLOR="Blue"]this[/COLOR]]("https://help.ubuntu.com/community/FirefoxNewVersion").
It sounds like maybe you missed a step.

-Xout

I read through that, and there are quite a few steps I cannot do.  For instance, I didn't have Firefox installed before so there is no totem-mozilla plugin, no old profile to rename, etc.  The rest of the steps I cannot do because there is no /usr/bin/firefox directory or file.

I'm sure I am missing something, but I am very new to this and I'm not sure what I should be doing differently?

---

### Post by Shatrat on 2007-01-24
Try launching it in a terminal like teitunge suggested.
Just type "firefox" and hit enter in the termina, if there are any errors they will print to the terminal.

---

### Post by crossedout on 2007-01-25
> I didn't have Firefox installed before

Since FF comes standard with Ubuntu, I am confused.  Did you uninstall FF at some point?

> The rest of the steps I cannot do because there is no /usr/bin/firefox directory or file.

Unless you truly did not have FF before your recent install, that file is there and you should check again.

> I'm sure I am missing something, but I am very new to this and I'm not sure what I should be doing differently?

No worries, being new just means more to learn.  Before breaking down exactly what you did during the install, follow teitunge's and Shatrat's advice on running it from the terminal and post the errors.  You should also take another look at that link I posted previously, focusing specifically on the symbolic link.  Regardless of having a previous version you'll need that link to make life easy.

Let us know what happens.
-Xout

---

