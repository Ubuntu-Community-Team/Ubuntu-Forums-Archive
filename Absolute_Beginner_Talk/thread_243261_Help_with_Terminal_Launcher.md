---
title: "Help with Terminal Launcher"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Ziggy72 on 2006-08-24
In a terminal I can type:

encfs ~/penc ~/pencv

And exactly what I want to happen does happen.

I would like to make a launcher which does the above by opening a terminal window, executing the above command and then the terminal window remains open.

I've tried putting a range of commands in the Create Launcher window, but nothing I've done seems to work, so help will be much appreciated. I'm using Gnome.

---

### Post by eternalsword on 2006-08-24
if this is gnome terminal, with gnome terminal open, go to Edit -> Current Profile  and then select the tab Title and Command, at the very bottom, there should be a When command exits option, choose the last one.

---

### Post by Ziggy72 on 2006-08-24
Thanks for the suggestion but if I do that, then surely that setting will affect *every* Gnome terminal which I open and that's not what I want. I want a launcher for just one Gnome terminal.

---

### Post by eternalsword on 2006-08-25
create a new profile, holdterm, with that option enabled and from the launcher do gnome-terminal --window-with-profile="holdterm" -x "encfs ~/penc ~/pencv"

---

### Post by Ziggy72 on 2006-08-25
Many thanks..

---

