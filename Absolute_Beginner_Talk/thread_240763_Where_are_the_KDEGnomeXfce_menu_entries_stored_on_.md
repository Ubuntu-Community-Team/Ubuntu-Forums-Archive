---
title: "Where are the KDE/Gnome/Xfce menu entries stored on my HDD?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by jamadagni on 2006-08-21
Hello. On Windows, I know my Start Menu entries go under the Start Menu folder under my Documents and Settings\<username> folder. I am able to relocate it, cut/copy/paste/delete the files directly, etc. 

Where do the menu go under KDE? I mean where are they saved in the tree-heirarchical order under KDE (and GNOME and Xfce, while we are at it)?

---

### Post by H.E. Pennypacker on 2006-08-21
I am not sure what the question is, so I'll ask this: exactly what are you trying to accomplish?  What you're looking for may not be available on Linux, but there may be another way of doing things.  

For example, there is no "Program Files" folder in a Linux directory, but we do have a folder called "bin", which functions much like Program Files.

---

### Post by jamadagni on 2006-08-21
OK maybe I shouldn't have posted my Q here. I'm not a Linux newbie exactly. I know that binaries go into bin directories, done console-mode package installations and everything. 

I am talking about the actual *entries* - the ones I edit by right-clicking on the KDE Menu icon and saying "Open KMenu Editor" - where I specify the name, description, launch feedback, run in terminal, run as different user etc settings. Where do these menu entries together with their settings get saved on my HDD?

I hope I put the question clearer now.

---

### Post by edrodgers731 on 2006-08-21
Try /etc/menu-methods for gnome.  I think the data is not in a file tree format.  /usr/share/doc/gnome-panel/README.Debian talks about a tool to manipulate the menus in your home directory, and then export to the gnome-panel.

Hope it helps..

---

### Post by ubername on 2008-03-30
I have a similar question. When I install software via synaptic (or other methods) it is automatically made available to all users on the machine. I would like to be able to change this so the less experienced members of my family don't have to wade through all the stuff I download on their Applications menu. If I could specify who should access the new stuff at download time that would be great, but at least knowing what to edit to keep their menus constant would be a start.

Any Clues?

TIA

---

