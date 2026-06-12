---
title: "Universe Repoistory"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by koz-man on 2007-05-10
Looking to enable the Universe Repoistory on my Ubuntu.
[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)
that tells me to edit a file.

can anyone walk me thru that?

Trying to get my laser printer and Ipod working, I understand I need to go to the Universe in order to download some additional items (gtkpod and some .deb converter program).

I am new with Ubuntu and everything is a first for me.

thanks

---

### Post by mikewhatever on 2007-05-10
You can do it graphically by going to System>Administration>Software Sources and checking the Universe box.
If you prefer the terminal, back up first
> sudo cp /etc/apt/sourses.list /etc/apt/sourses.list_backup
and then
> gksudo gedit /etc/apt/sourses.list

---

### Post by Najand on 2007-05-10
The easiest way it to go to:
System -> Administration -> Software sources

And check all boxes on the page with "Ubuntu Software" tab.

---

### Post by koz-man on 2007-05-16
thanks. problem solved.

---

