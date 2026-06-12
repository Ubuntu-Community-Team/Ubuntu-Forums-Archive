---
title: "Beagle won't launch applications"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by mnewsom on 2007-08-03
I've searched the forums but I couldn't find a fix for my particular problem. I want to launch applications through Beagle. I added /usr/bin to the index in beagle-settings. Beagle finished indexing and finds all my applications but it calls them documents instead of applications. When I try to launch something nothing happens. Running beagle-search from the terminal displays an error when I try to launch.
Can't open MimeType 'application/x-execuatable'
Any suggestions?

---

### Post by zanglang on 2007-08-03
You don't have to add /usr/bin to be indexed, Beagle is supposed to automatically look for and update a list of applications (although just limited to GUI apps) installed automatically.

Try Deskbar (package 'deskbar-applet') if you're looking for a commandline launcher, it's much faster and integrates well on the desktop.

---

### Post by mnewsom on 2007-08-03
Thanks! Deskbar works well as a launcher. When I was browsing through the forums I got the impression that Deskbar was an addition to Beagle but I guess its the other way around. 
I am having a little trouble getting Deskbar to find my files. I've clicked "Files, folders & places" in the preferences but its not finding a file I put on my desktop. Would using Beagle through Deskbar solve this?

edit - yes.

---

### Post by zanglang on 2007-08-03
Yeah, it may be a little confusing when you first start using it. And Deskbar and Beagle are unrelated projects by the way, Deskbar is under GNOME, and Beagle sort of falls under the Mono project. :P

'Files, Folders and places' only returns files inside your home folder, recently used documents and a bunch of locations you would use on Nautilus. I've had problems getting it to locate files properly as well. For this I would recommend 'Beagle Live' deskbar extension, which searches while you type (if you can't see it, install 'python-beagle' and then type 'killall gnome-panel').

---

