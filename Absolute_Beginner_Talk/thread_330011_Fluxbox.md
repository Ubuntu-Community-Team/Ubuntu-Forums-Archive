---
title: "Fluxbox"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by FSX on 2007-01-02
Can I install Fluxbox on Xubuntu 6.10 edgy? And can I do this with Synaptic?
And when I installed Fluxbox is Xfce gone?
And can switch to Xfce from Fluxbox and from Xfce to Fluxbox?

*My english is really good.*

---

### Post by bodhi.zazen on 2007-01-02
Yes you can install Fluxbox.

When you log in (at the log-in screen) you may choose either fluxbox or XFCE (choose session type).

You can run both:

[http://www.ubuntuforums.org/showthread.php?&t=271674](http://www.ubuntuforums.org/showthread.php?&t=271674)

---

### Post by FSX on 2007-01-03
But how van I configure Fluxbox.

In Fluxbox was no menu. The only thing I can do is switch between workspaces.
In '/etc/X11/fluxbox' and '/home/frank/.fluxbox' are menu files. Wich one do I need to edit?

---

### Post by Sef on 2007-01-03
Read the [Fluxbuntu wiki]("http://wiki.fluxbuntu.org/index.php?title=Main_Page") to start.

---

### Post by bodhi.zazen on 2007-01-03
> **FSX said:**
> But how van I configure Fluxbox.

In Fluxbox was no menu. The only thing I can do is switch between workspaces.
In '/etc/X11/fluxbox' and '/home/frank/.fluxbox' are menu files. Wich one do I need to edit?

LOL FSX :p

You have several options.

First /etc/X11/fluxbox/menu is a system file and, as with all files in /home, /home/frank/.fluxbox/menu is used by you.

Often the menu in /home referances the one in /etc.

So your first option is to copy /etc/X11/fluxbox/menu to /home/frank/.fluxbox/menu

Second option is to generate a menu. You can use fluxbox-generate_menu or menumaker.

Here is a link to a how-to on menumaker:

[How to menumaker](http://community.fluxbuntu.org/index.php?&topic=36.0)

Last, you can write one yourself (which is what a lot of fluxbox users do).

There are several gui configuration tools, search fluxbox in synaptic .....

Also the above link should help.

HTH 8)

---

### Post by bodhi.zazen on 2007-01-03
FSX FYI that application is fluxconf.

Fluxconf includes:

fluxkeys - gui to set hot keys

fluxmenu - gui to edit your menu

fluxbare - A gui to launch fluxkeys, fluxconf, or fluxkeys.

Welcome to Fluxbox :p

HTH 8)

---

### Post by FSX on 2007-01-04
Thanks, now I get it :D.

---

