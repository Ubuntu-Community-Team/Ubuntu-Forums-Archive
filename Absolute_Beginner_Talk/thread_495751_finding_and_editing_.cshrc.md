---
title: "finding and editing .cshrc"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by horowitz53217 on 2007-07-08
I have a program i need to install and use called Autodock, and there is one line of the installation process that i am having trouble with:
[COLOR="DarkSlateBlue"]
NOTE: To run AutoDock on Linux and Mac OS X machines, you
must put the following line in your “.cshrc” or “.login” file:

limit stacksize unlimited[/COLOR]

I know that .login and .cshrc are supposed to be in my home folder and hidden, but i still can't find them when i hit "display hidden files" in the file browser.  I tried opening the file in the terminal with 

"gedit /.cshrc"

But the file that it opens is completely empty!  Is this right?

Any help would be greatly appreciated.

---

### Post by taurus on 2007-07-08
```
gedit ~/.cshrc
```

---

### Post by horowitz53217 on 2007-07-08
Tried 

gedit ~/.cshrc

but it didn't work, i still get a file that's totally empty.

---

### Post by jyba on 2007-07-08
If it's totally empty that means that no .cshrc has been created yet, so you need to create it yourself. 

Just type...
```
gedit ~/.cshrc
```
then paste... 
```
limit stacksize unlimited
```
...into it, and save it.

---

