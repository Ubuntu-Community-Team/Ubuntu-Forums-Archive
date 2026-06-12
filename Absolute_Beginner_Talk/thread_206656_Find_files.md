---
title: "Find files"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by omono on 2006-06-30
I'm new to Linux. I intalled the juno.deb through terminal using dpkg -i command. Terminal showed it was a successful install but I cannot find the files to launch. How do I locate it? Thanks....

---

### Post by richbarna on 2006-06-30
[QUOTE=omono]I'm new to Linux. I intalled the juno.deb through terminal using dpkg -i command. Terminal showed it was a successful install but I cannot find the files to launch. How do I locate it? Thanks....[/QUOTE]

Try pressing Alt+F2 and typing juno in the start box.

---

### Post by gezzabob on 2006-06-30
the command locate <filename> may give you the info you are looking for.

ps you may want to update the indexing database of files for locate before running the locate command simply  type sudo updatesb and supply your password as normal, give that a few seconds to re-index your files so locate knows about them.

hope this helps.

---

### Post by catlett on 2006-06-30
You can also run an application from the terminal by entering it's name. i.e. to launch firefox enter this```
 firefox
``` If you just want to know where files are t you can use thw whereis command i.e. to see where firefox files are enter this in the terminal ```
whereis firefox
``` I like the debian menu. It lists alot more than the gnome menu.

---

### Post by siccness on 2006-06-30
find / -iname "*fire*"

:-)

---

