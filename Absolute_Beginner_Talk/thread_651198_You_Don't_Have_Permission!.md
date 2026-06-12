---
title: "You Don't Have Permission!"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by johnfarrow on 2007-12-27
[FONT="Arial Black"]:)
I want to save a gedit file in "Home".  Says I dont have permission.
Using 7.04.  I am only user.  What to do? 












[/FONT]

---

### Post by taurus on 2007-12-27
Home as in /home/*your_username*?

---

### Post by johnfarrow on 2007-12-27
NO, just home

---

### Post by taurus on 2007-12-27
And where exactly is that home?  Remember, you can only write to your own $HOME directory.  If you want to save files outside of your $HOME directory, you need to be root and to fix that, you would use sudo/gksudo.

So, run gedit with gksudo in front of it then.

Applications -> Accessories -> Terminal
```
gksudo gedit *filename*
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by PmDematagoda on 2007-12-27
To save a file in /home you will need to open Gedit in root mode, this can be done using:-
```

gksudo gedit
```

But why do you need to create a file in /home? The place where your files and settings are stored is in /home/yourusername and using /home is just a waste of time and is simply pointless.

---

### Post by johnfarrow on 2007-12-27
Because its a file I want quick access to and /home/user already has a lot of files in it and I need to search for it in /home/user

---

### Post by PmDematagoda on 2007-12-27
If it is quick access you are looking for, then wouldn't it be more sensible to create the file on the desktop?

---

### Post by taurus on 2007-12-27
Then why not create another directory to store your new files in /home/user/new.

Applications -> Accessories -> Terminal
```
mkdir ~/new
```
Now, you can save whatever new files you want to ~/new without worrying about permissions.

---

### Post by johnfarrow on 2007-12-27
OK.  On the desktop.  Thats it!  Thanks guys

---

### Post by PmDematagoda on 2007-12-27
Glad we could help you make up your mind:).

---

