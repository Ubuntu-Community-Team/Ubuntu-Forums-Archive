---
title: "Flash Player 9 plugin"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by jasonsexton on 2006-11-19
can someone tell me step by step how to install the flash player 9 plugin for firefox?  when I drop the plugin file into the plugins folder for firefox, it says I don't have permission to copy to that folder.
thanks.

---

### Post by sbassett on 2006-11-19
Via terminal or konsole, you would simply append sudo to the command.

```
 sudo cp /path/to/plugin.so /usr/lib/mozilla/plugins/ 
```

worked just fine for me.

---

### Post by junglepeanut on 2006-11-19
It sounds like you want to use a file manager like nautilis or something like that.

Start it with gksudo to give it root privileges but be careful.

Or just use the comand line

sudo cp fileplace/filename tofileplace/filename

---

### Post by jasonsexton on 2006-11-19
thanks!

---

### Post by bilange on 2006-11-19
If you're not quite at ease with the command line, you can drop the plugin file into /home/**yourname**/.mozilla/plugins. 

Click on "places", "Personal folder" (the first item in the list). If you don't see hidden folders (those starting with a dot character) press Ctrl+H, and go to .mozilla/plugins. Copy the library there.

Restart Firefox and enjoy :)

Automatix installs the flash libraries in this exact directory, too, so it may not be impossible to see other flash libraries there already. You may want to remove them (back them up) from this folder, to prevent having some kind of comflict between Flash 7 and 9.

---

