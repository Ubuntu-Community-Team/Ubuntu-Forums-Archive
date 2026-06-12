---
title: "installing gedit 2.14"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by gatorbrit on 2006-04-06
I want to install the newest release of gedit - version 2.14.  I have the tar.gz file.  What should i do now?

Thanks

---

### Post by gatorbrit on 2006-04-06
Actually I should be more specific.  I unzipped the file in a temp dir, typed
**./configure**
And I get this error....
> checking for GEDIT... configure: error: Package requirements (
        glib-2.0 >= 2.8.0
        gtk+-2.0 >= 2.8.0
        gtksourceview-1.0 >= 1.2.0
        libgnomeui-2.0 >= 2.13.0
        libglade-2.0 >= 2.4.0
        libgnomeprintui-2.2 >= 2.6.0
        gnome-vfs-2.0 >= 2.13.4
) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GEDIT_CFLAGS and GEDIT_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

---

### Post by linear on 2006-04-06
Have you checked that you have the correct versions of all the dependencies? For example, libgnomeui appears to be at 2.12.0 in Breezy.
 
Tracking them down may be a chore.

---

### Post by gatorbrit on 2006-04-06
[QUOTE=linear]Have you checked that you have the correct versions of all the dependencies? For example, libgnomeui appears to be at 2.12.0 in Breezy.
 
Tracking them down may be a chore.[/QUOTE]

You know what - I think that this is problem and frankly I don't think that it is worth the effort... I guess I'll stick with the earlier version for now.

Thanks for the feedback...

---

