---
title: "Vlc [Resolved]"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by frostbytes on 2007-06-01
I need help setting VLC as the default media player for streaming in firefox. Having a few problems playing .wmv files and I read somewhere that VCL played them like a champ.  I know how to switch back and forth between totem and mplayer using the quarentine folder, just dont know how to get VLC to work.....
Im a little new at this, so dumb it down like you would to a 2nd grader....thanks for your posts!!

---

### Post by aysiu on 2007-06-01
Go to System > Administration > Synaptic Package Manager > Settings > Repositories and make sure the Universe (Community Maintained) repositories are checked. Then click Reload. Then search for, mark for installation, and apply changes for the package *mozilla-plugin-vlc*

In Firefox, go to Edit > Preferences > Content > File Types > Manage and select .wmv and find Open them with this application and look for VLC in /usr/bin

---

### Post by frostbytes on 2007-06-03
appricate it man....worked like a charm.....started reading ur blog, good stuff....again, thanks alot

---

