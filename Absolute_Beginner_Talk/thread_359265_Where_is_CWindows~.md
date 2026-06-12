---
title: "Where is C:\Windows\~?"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by oo-boon-too on 2007-02-11
I downloaded wine using the add/remove programs, it is installed and i have also installed a game or two. Only problem I have is: Where in the world is C:\?
I'm fairly new to the linux filesystem, so I just looked eveywhere i could but still didnt see it.
Any help would be greatly appreciated.

---

### Post by jordanmthomas on 2007-02-11
look in 
```
~/.wine
```
it should make itself evident (I'm thinking maybe a folder called drive_c or something similar)

---

### Post by shareMenaPeace on 2007-02-11
Its inside the wine folder

either search with 
whereis wine or locate wine

or open nautilus the home folder and hit CTRL + H to see hidden files.

---

### Post by oo-boon-too on 2007-02-11
Ah thank you both very much, ive gotta get used to this:P
Found it and did what was needed:)
Thanks again~

---

### Post by Norfolk 'n' Good on 2007-02-11
Go to Places>Home Folder... when the Home screen opens hold down CTRL and press h.  All the hidden files (called dot files) will appear.  Scroll down until you see .wine.  If you open that folder you will see a folder named 'C'.  Inside there is what you would normally expect to see on you C drive in Windows.

Hope that helps.

---

