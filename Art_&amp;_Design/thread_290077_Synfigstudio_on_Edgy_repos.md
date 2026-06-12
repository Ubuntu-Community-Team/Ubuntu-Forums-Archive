---
title: "Synfigstudio on Edgy repos"
date: 2006-10-31
forum: Art &amp; Design
---

### Post by uuwatti on 2006-10-31
Has anyone managed to get synfigstudio working? I tried building it on Dapper, but that didnt work (the program started, but none of the tools worked). And now that I saw on edgy repos I tought that it would work, but the result is even worse. Now there are no icons and the tools still dont work. Is this a bug in the program or am I just plain stupid? The program itself looks pretty promising vector animation program.

---

### Post by ciscosurfer on 2006-10-31
> **uuwatti said:**
> Has anyone managed to get synfigstudio working? I tried building it on Dapper, but that didnt work (the program started, but none of the tools worked). And now that I saw on edgy repos I tought that it would work, but the result is even worse. Now there are no icons and the tools still dont work. Is this a bug in the program or am I just plain stupid? The program itself looks pretty promising vector animation program.

I'm having a similar issue...will investigate and get back to you when** I figure something out 8)

---

### Post by kperkins on 2006-10-31
Same problem here. Using Edgy.

---

### Post by Flochette on 2006-11-03
Hello all!
I've the same problem in edgy no icons on the buttons but the tools seems to work. I think it's a library... I've this text when i launch it in a terminal:
```
synfig(7067): info: DockManager::register_dockable(): Registered dockable "tool_options"
synfig(7067): info: DockManager::register_dockable(): Registered dockable "history"
synfig(7067): info: DockManager::register_dockable(): Registered dockable "canvases"
synfig(7067): info: DockManager::register_dockable(): Registered dockable "keyframes"

(synfigstudio:7067): Gtk-WARNING **: node type doesn't match 2 (menu-main is type 7)
synfig(7067): info: DockManager::register_dockable(): Registered dockable "layers"
synfig(7067): info: DockManager::register_dockable(): Registered dockable "params"
synfig(7067): info: DockManager::register_dockable(): Registered dockable "meta_data"
synfig(7067): info: DockManager::register_dockable(): Registered dockable "children"
synfig(7067): info: DockManager::register_dockable(): Registered dockable "info"
synfig(7067): info: DockManager::register_dockable(): Registered dockable "navigator"

(synfigstudio:7067): GLib-GObject-WARNING **: value "inf" of type `gdouble' is invalid or out of range for property `step-increment' of type `gdouble'

(synfigstudio:7067): GLib-GObject-WARNING **: value "inf" of type `gdouble' is invalid or out of range for property `page-increment' of type `gdouble'
synfig(7067): info: DockManager::register_dockable(): Registered dockable "timetrack"

(synfigstudio:7067): GLib-GObject-WARNING **: value "inf" of type `gdouble' is invalid or out of range for property `step-increment' of type `gdouble'

(synfigstudio:7067): GLib-GObject-WARNING **: value "inf" of type `gdouble' is invalid or out of range for property `page-increment' of type `gdouble'
synfig(7067): info: DockManager::register_dockable(): Registered dockable "curves"
synfig(7067): info: DockManager::register_dockable(): Registered dockable "groups"
synfig(7067): info: Input device changed to "Core Pointer"
synfig(7067): info: DockManager::register_dockable(): Registered dockable "pal_edit"
synfig(7067): info: DockManager::register_dockable(): Registered dockable "pal_browse"
synfig(7067): info: dock_book_list.size()=1
synfig(7067): info: dock_book_list.size()=2
synfig(7067): info: dock_book_list.size()=3
synfig(7067): info: dock_book_list.size()=4
synfig(7067): info: dock_book_list.size()=1
synfig(7067): info: dock_book_list.size()=1
synfig(7067): info: dock_book_list.size()=2
synfig(7067): info: Distance::Distance(): ret=1, val=1,000000
synfig(7067): warning: Settings::load_from_file(): Key "window.color.pos" with a value of "" was rejected.
synfig(7067): warning: Settings::load_from_file(): Key "window.color.size" with a value of "" was rejected.
synfig(7067): warning: Settings::load_from_file(): Key "window.gradient.pos" with a value of "" was rejected.
synfig(7067): warning: Settings::load_from_file(): Key "window.gradient.size" with a value of "" was rejected.
synfig(7067): info: PID=7144 has been cleaned up
synfig(7067): info: PID=7229 has been cleaned up
synfig(7067): info: PID=7324 has been cleaned up
synfig(7067): info: PID=7399 has been cleaned up
```

i've verified all the dependencies it needs...
i will post if i find something...

---

### Post by -Phi- on 2006-11-16
After wandering around the web doing research, I believe the issues are due to [this lovely little unresolved bug right here]("http://sourceforge.net/tracker/?func=detail&aid=1509627&group_id=144022&atid=757416"). Presumably the edgy .debs were compiled using gcc 4.1, leading to .png render failures and missing icons.

Also, the vectors don't remember where they're supposed to go when you save or export files (possibly a separate bug).

- Phi

---

### Post by uuwatti on 2006-11-16
yep, but they say its fixed in the svn. i already compiled it from svn back then and the problem wouldn't go away. i'll try again later today.

---

### Post by -Phi- on 2006-11-16
I'm pretty sure the [fesity .debs](https://launchpad.net/distros/ubuntu/feisty/+search?text=synfig) have these problems fixed. Of course, you can't install them without upgrading half your system... maybe someone will backport it.

For now a quick bandaid fix for the icons is to unzip working icons into /usr/share/pixmaps (synfig doesn't seem to make its own pixmap directory. odd). See attached.

Of course, fixing the icons doesn't fix anything else. Apparently the vector issue is in the compiling of loadcanvas.cpp. Presumably copying libraries from the Feisty deb in a similar way as copying the icons is a bad idea?

- Phi

---

### Post by uuwatti on 2006-11-16
you are right loadcanvas.cpp doesn't compile correctly. the problem isn't fixed in the svn either (just tried it). also i can't find any solution to it. EDIT: well they say its fixed so it can't be that... or can it?
EDIT2: i will stop trying to compile it now, no matter what i do, the tools just won't work. I'll give backporting it from feisty a try later and then i'm done.

---

### Post by Dooglus on 2007-10-11
It's fixed now, and in the most recent release of synfig, 0.61.07.

---

