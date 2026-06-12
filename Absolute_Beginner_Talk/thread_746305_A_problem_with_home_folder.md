---
title: "A problem with home folder"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Feli26 on 2008-04-05
Hey all, im having a little issue, i installed eve online (game) it installed well, but  when i update it, i get this error: 

[B]An error occurred while trying to apply an update to EVE Online for Linux. The directory /home/feliberto/.cedega/EVE Online does not seem to exist. If you renamed the folder, please unrename it. If that doesn't work, you might need to obtain a fresh install of the game.
[/B]


I get into the home folder and search, i didn't see anything... i tried to make a folder with .cedega name and it said that i already had a folder with that name, "Crazy"...
i reinstalled all and still have the same problem...

This isn't the first time i get this problem, i don't get the ~/.file thingy in the majority of my installs. i don't have the ~/.amsn neighter... Something invisible?

I hope any of you could help me, i will appreciate it a lot, thanks...:popcorn:

---

### Post by Doorslammer on 2008-04-05
the folder is hidden in your home directory 
anything with a dot & slash is hidden 
in the file menu  click view then unhide you will see the directorys  that are hidden
or simply  ctrl+H will unhide

---

### Post by TeoBigusGeekus on 2008-04-05
Folders with a dot (.) in front of their name are hidden folders in Ubuntu. Open your /home folder with Nautilus and press Ctrl+H to reveal them.

---

### Post by amingv on 2008-04-05
Folders that start with a '.' in Linux/Unix are hidden files or folders. To see these folders you can go to View>Show Hidden Files (or Ctrl+H) in Gnome/Nautilus or View>Show Hidden Files (Alt + .) in KDE/Dolphin.

You can see them in the terminal using the -a parameter, too:

```
ls -a
```

---

### Post by Feli26 on 2008-04-05
Ah, i see them now, thanks alot guys =]!! well the folder is there so, i dont know why it doesn't work.. uhhhh patience =b!

---

