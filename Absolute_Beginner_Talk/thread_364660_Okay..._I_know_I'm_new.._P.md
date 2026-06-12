---
title: "Okay... I know I'm new.. :P"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by StarscreamD on 2007-02-18
I installed Sun Java on Ubuntu Edgy and the install made a folder on my desktop that is locked. The permissions say that root owns the folder and I cannot delete it or move it. First off, I assume root is the admin account..? How do I get this folder off of my desktop? Thank you.

---

### Post by TriggerHappyChewie on 2007-02-18
Open a Terminal:

Applications > Accessories > Terminal

and type this in:

```
cd ~/Desktop
```

then

```
sudo rm -r FOLDERNAME
```

where FOLDERNAME is the exact name of the folder.
It will ask you for your password, which will just be your normal user password.

---

### Post by picpak on 2007-02-18
Hit Alt+F2. In the run box, type

```
gksudo "nautilus --browser %U"
```

and hit enter. Type in your password. Go to the desktop folder, and delete the folder in question.

To save yourself the trouble, you can create a shortcut to this command.

---

### Post by IYY on 2007-02-18
Well, you can remove the folder with
```

sudo rm -rf ~/Desktop/FolderName
```

but what sort of folder is it? Could it be important?

---

### Post by StarscreamD on 2007-02-18
Hey, that worked great, thanks guys!

---

### Post by StarscreamD on 2007-02-18
I suppose it could of been important :P It had Sun Java stuff in it, and the plugin seems to be installed correctly still.

---

