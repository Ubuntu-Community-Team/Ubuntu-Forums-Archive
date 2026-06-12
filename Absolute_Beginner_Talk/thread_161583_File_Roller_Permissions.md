---
title: "File Roller Permissions"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Quicky on 2006-04-17
Hi, I'm a new linux user and am for the moment trying to avoid using the terminal as much as possible until I get a bit more used to the platform, but I'm struggling with File Roller. Double clicking on a zip file opens the program, but I cannot extract to a protected folder; it gives an "Extraction not Performed" error saying that I do not have the correct permissions.

Is there a way to start File Roller with root access, or type in the sudo password at any point in order to allow this action?

Any help would be appreciated.

---

### Post by htinn on 2006-04-17
If you don't have permissions to extract, there's probably a really good reason for it. Sending the contents of a random zip file into your system folders can destroy your system. Careless unpacking to someone else's folders can damage their data and/or configurations.

Now, if you don't really care about all that, then feel free to press Alt+F2 and type the following:

gksudo file-roller

That will get the program running in root.

---

### Post by Quicky on 2006-04-17
Thanks, I've just tried that, but running File Roller with that command preceding it resulted in the program not being able to find the zip file when I click open. The file I'm trying to unzip is on my desktop, but file roller does not seem to be able to see them. If I run file roller without that command, it can see them fine? Do you know why this could be happening?

Incidentally, what does the gk part of the command mean? How does it differ from just stating sudo?

---

### Post by Conspiritor on 2006-04-17
"gk" infront of the "sudo" is used for Gnome windows.

You'd use this, for example, when you want to open Gedit as root.

---

