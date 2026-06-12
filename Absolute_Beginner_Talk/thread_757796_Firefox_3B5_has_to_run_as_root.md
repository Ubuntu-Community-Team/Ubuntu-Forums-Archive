---
title: "Firefox 3B5 has to run as root?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by coderdb on 2008-04-17
I've just "installed" Firefox 3B5 by copying over the firefox folder in the download from Mozilla into usr/lib using Nautilus as root, but I need to now run the firefox script as root too. Is there a way to remove that from the firefox file? It's a fresh install of Ubuntu Gutsy, this is literally the first thing I've done.

---

### Post by ByteJuggler on 2008-04-17
You should probably not do that, it messes with what the package manager knows is installed and will almost certainly break your updates/upgrades.  Instead, you should install the package alongside the existing firefox, probably in /opt (which is where manually/optionally installed packages are traditionally put.)

I don't offhand know how i'd fix what you've done to your install though. I'd almost suggest reinstalling but that's overkill.   Probably I'd rather try to delete the folder again, and try uninstalling firefox with Synaptic, then reinstalling, which should put everything back in place.

Anyway, I'm guessing the root thing is a permissions issue.  Check whether the file is world executable. (This is for when you've put the thing in the right place, e.g. in /opt)

---

### Post by konungursvia on 2008-04-19
Me too, I can't run firefox without being sudo/root, except swiftweasel. I notice that many apps, including ff, frostwire, thunderbird, deluge... won't run yet in hardy-64 for me, and they all seem to lack permission to write to .files according to the various error messages.

---

### Post by konungursvia on 2008-04-19
Noticed something new while command line installing firefox-2 in an attempt to fix this: An error message relating to gxine that seems to be the problem:

File '/usr/share/applications/gxine.desktop' contains invalid MIME type 'x-content/video-vcdx-content/video-vcd' that has more than one slash
Please restart any running Firefoxes, or you will experience problems.

How to fix this I wonder?

---

