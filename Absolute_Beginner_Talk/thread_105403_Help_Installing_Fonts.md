---
title: "Help Installing Fonts"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by the_purulent on 2005-12-18
I'm trying to copy a new font into the fonts:/// location as per the directions in the ubuntu guide, but I don't have permission to copy.  If I try in the terminal it tells me that fonts:/// is not a directory?

How can I get these installed?

---

### Post by poptones on 2005-12-18
just make a fonts folder in your home directory falled .fonts (important it has the dot - it will be hidden) and copy your fonts there. although your desktop (gnome) itself won't see them until you log out and back in again, the applications like gimp and gedit will see them immediately.

mkdir ~/.fonts
cp *a/buncha/fonts* ~/.fonts

To see these folders in nautilus select "show hidden files."

---

### Post by the_purulent on 2005-12-18
awesome! thanks

---

