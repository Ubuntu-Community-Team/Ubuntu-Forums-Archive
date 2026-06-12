---
title: "Recusively Delete Files?"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by pmghalvo on 2007-09-02
I have an external drive and put everything in my My Music folder on it for backup, however, I'm running out of room. I want to go through and delete all the image files out of it. The problem is I have sub-folders of sub-folders.

I've been using:
```
rm *.jpg
```
to get rid of them in each individual folder, but it is taking a long time to navigate through each folder. I was wondering if there was a way were I could recursively go through each folder and delete all .jpg files with a single command. Or if I would have to write my own script to do this.

---

### Post by aysiu on 2007-09-02
Close the terminal.

Use a search in the graphical interface (using Gnome or KDE's search tool) for *.jpg in the My Music folder.

Once the search is done, delete all the results.

---

### Post by pmghalvo on 2007-09-02
Thankyou,

I've been trying to get used to using more terminal then GUI lately, that's why I was looking for a command line solution.

---

### Post by Dr Small on 2007-09-02
You could try:
```
rm -R /path/to/folder/*.jpg
```

Dr Small

---

### Post by banewman on 2007-09-02
To find out the options for - rm - in terminal type - man rm - the options I see only allow file or directory & files removal. Wouldn't try rm -r  /path/to/dir *.jpg without a backup just in case it removes the directory.

---

### Post by Dr Small on 2007-09-02
It will not remove the directories. Just any file in that specific directory with the extension of .jpg. That's why it is *.jpg.

I use it when backing up my xchat logs, and here is an example:
```
cd $HOME/.xchat2/
FILENAME=`date '+%m%d%y'`
tar -cvvf xchatlogs/$FILENAME.tar xchatlogs/*.log
rm xchatlogs/*.log
```

Dr Small

---

