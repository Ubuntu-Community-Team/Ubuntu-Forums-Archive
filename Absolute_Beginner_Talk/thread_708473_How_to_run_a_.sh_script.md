---
title: "How to run a .sh script?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by talvon on 2008-02-26
I've installed KDE desktop to try again, as I prefer it to the gnome one, but I installed it through gnome and now all the KDE apps are back in the gnome menus. I found this:

[http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/](http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/)

To get rid of them, and I downloaded the script, but I can't run it :|

I've manually made it executable by right-clicking it and going to properties, cd'D to my desktop with the Terminal (Where the script is), and I type:

```
sudo sh menu-cleaner.sh
```

And I get 'can't open menu-cleaner.sh', and if I try bash instead of sh I get no such file or directory.

Any help would be appreciated :P

Thanks :)

---

### Post by kryth on 2008-02-26
there's other ways... but here's how i do it

chod +x nameOfFile
then just type the name of the file
or

bash /home/user/fullPathToTheFile

not 100% on syntax of last way.

---

### Post by talvon on 2008-02-26
Ace, cheers :D

The 1st method worked for some reason, I'm was sure that's what I was trying before lol. Big success :P

---

