---
title: "Uninstalling GAIM"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2007-03-14
Gaim has been giving me problems so I changed to Kopete, when I go to synaptics and try to unstill it that way it also tries to uninstall xubuntu-desktop :( How can I just get rid of GAIM? Im tired of it popping up automatically on startup (even though its not a startup application)
Would it be prudent to just delete the .gaim directory in my home? Im still quite new to linux/ubuntu so Im not sure if thats the proper way of disposing of applications. :)

---

### Post by ciscosurfer on 2007-03-14
> **Daergeth said:**
> Gaim has been giving me problems so I changed to Kopete, when I go to synaptics and try to unstill it that way it also tries to uninstall xubuntu-desktop :( How can I just get rid of GAIM? Im tired of it popping up automatically on startup (even though its not a startup application)
Would it be prudent to just delete the .gaim directory in my home? Im still quite new to linux/ubuntu so Im not sure if thats the proper way of disposing of applications. :)When Synaptic says that it is going to remove xubuntu-desktop when you go to remove Gaim, that's okay.  Xubuntu-desktop is simply a meta-package.  When you go to do an update of your system, simply download xubuntu-desktop again (which will already be in your apt cache anyhow unless you delete that as well).  Bottom line, it's okay to delete xubuntu-desktop when you remove Gaim.

Alternatively, you can go into Sessions and disable the Gaim app from starting (in other words, you won't have to remove Gaim at all, just disable it from startup).

---

### Post by Belyel on 2007-03-14
> **ciscosurfer said:**
> When Synaptic says that it is going to remove xubuntu-desktop when you go to remove Gaim, that's okay.  Xubuntu-desktop is simply a meta-package.  When you go to do an update of your system, simply download xubuntu-desktop again (which will already be in your apt cache anyhow unless you delete that as well).  Bottom line, it's okay to delete xubuntu-desktop when you remove Gaim.

Alternatively, you can go into Sessions and disable the Gaim app from starting (in other words, you won't have to remove Gaim at all, just disable it from startup).

I'm going to expand on this a little, cause I was confused by this same problem.  The xubuntu-desktop is a metapackage, yes.  This means that it doesn't really contain any programs, but it contains the links to all of the programs that are part of xubuntu's desktop.  The package, when installed, automatically finds and installs everything linked in the metapackage.  When you want to uninstall something that was part of the metapackage, apt sees that the metapackage is no longer needed, so it gets rid of it, leaving all your programs 100% intact.

There is probably an option somewhere in Gaim to have it start when you log in.  If you decide not to install it, look for that option and uncheck it.  If you can't find that, then check your "sessions" settings (I'm not sure if/where that is in xubuntu), and make sure there's not entry for it there.

---

### Post by ciscosurfer on 2007-03-14
> **Belyel said:**
> I'm going to expand on this a little, cause I was confused by this same problem.  The xubuntu-desktop is a metapackage, yes.  This means that it doesn't really contain any programs, but it contains the links to all of the programs that are part of xubuntu's desktop.  The package, when installed, automatically finds and installs everything linked in the metapackage.  When you want to uninstall something that was part of the metapackage, apt sees that the metapackage is no longer needed, so it gets rid of it, leaving all your programs 100% intact.

There is probably an option somewhere in Gaim to have it start when you log in.  If you decide not to install it, look for that option and uncheck it.  If you can't find that, then check your "sessions" settings (I'm not sure if/where that is in xubuntu), and make sure there's not entry for it there.Well said Belyel :-)

---

