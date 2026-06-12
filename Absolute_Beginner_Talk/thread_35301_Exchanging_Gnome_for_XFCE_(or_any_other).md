---
title: "Exchanging Gnome for XFCE (or any other)"
date: 2005-05-18
forum: Absolute Beginner Talk
---

### Post by zenlord on 2005-05-18
First off: I like Gnome very much, but I might consider XFCE for an older pc I have here (and for the sake of testing/experimenting of course).

But, let's say I have my Ubuntu fully configured for my needs, will all my settings and installed packages be ready available through another windows manager like XFCE? I do understand that Gnome-specific settings will be 'lost', but will I have to install certain packages again after changing?

Is it useful to have more than one window manager on top of the same kernel?

THX!

Zl.

---

### Post by az on 2005-05-18
"Is it useful to have more than one window manager on top of the same kernel?"

Good question!

The kernel is just a program.  It is the one program that runs all the others.  It is very low-level in that it has nothing to do with gnome, kde or XCFE.  

Is it useful to have more than one desktop environment installed?  That depends on your needs.  In your case I am sure that it is.

You can keep all the advantages that the gnome tools give you, but only use them when you need them.

If you install the XFCE4 package, you will have another desktop environment on your system.  To use it, just thell GDM (Gnome desktop Manager) to use it.  Before you login, click on session and pick a different session (XFCE session once you have it installed)

You can always go back to full-blown gnome by logging out and doing the same thing again.  You can run Gnome apps in XFCE, of course.

---

### Post by foxy123 on 2005-05-18
I've got Gnome, KDE and XFCE on my Ubuntu box, each for every family member. Personally I usually use xfce, but sometimes switch to Gnome.

Most of the configuration is available in all 3. However, there are some specific stuff, which needs to be configured for some of them, namely for xfce. For example, gdesklets does not start automatically in xfce as it does in gnome. So you have to put a script in Autostart. Menues in xfce are also behave  wierdly. At least you do not have all gnome entries there and I guess have to put some manually.

But overall, most of stuff works regardless of which window manager you use.

---

### Post by zenlord on 2005-05-19
THX for your answers!

I didn't get the chance yesterday to try it out, but this weekend will be filled with another set of linux-experiments!!

I'm very interested in making a very light weight OS (to turn an older pc into an internet/emailing machine for my mother to tamper with :p), so starting with an UBUNTU 'server-install', adding some required packages and installing a windowmanager like XFCE or IceWM would do just about that I presume?

Zl.

---

### Post by poofyhairguy on 2005-05-19
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

---

### Post by zenlord on 2005-05-19
[QUOTE=poofyhairguy][http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)[/QUOTE]
 THX for this excellent guide!

A first look tells me I was right globally, but it will surely help to know the package names!

The only difference for Hoary should be that the 'custom' command is not supported, but the 'server' command is if I'm not mistaken?

/EDIT: my bad, the 'custom' command is still supported!!!

Zl.

---

