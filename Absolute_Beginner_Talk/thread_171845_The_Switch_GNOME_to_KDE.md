---
title: "The Switch: GNOME to KDE"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-05-07
Hi,

I was wondering how I would go about changing Gnome to Kde on my laptop.

Would it delete any files or preferences? 

What are the advantages of Kde over Gnome?

What kind of problems would arise?

Many, many thanks as I know this is quite a big question.

---

### Post by kingmonkey on 2006-05-07
no need to delete anything, both can co-exist. 

I dont know what the advantages are, its just what you prefer. 

No problems will arise other than disk space more disk space.

Just type:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by Rinzwind on 2006-05-07
Hmm if you have both your gdm will also have kde programs in its menu.
Kde will also have gnome programs in its menu.

sudo apt-get uninstall ubuntu-desktop

deletes gdm btw :)

---

### Post by jrib on 2006-05-07
[QUOTE=Rinzwind]Hmm if you have both your gdm will also have kde programs in its menu.
Kde will also have gnome programs in its menu.

sudo apt-get uninstall ubuntu-desktop

deletes gdm btw :)[/QUOTE]

removing ubuntu-desktop using apt-get won't actually do anything because it's a meta package

---

### Post by Rinzwind on 2006-05-07
[QUOTE=_jason]removing ubuntu-desktop using apt-get won't actually do anything because it's a meta package[/QUOTE]


Shoot you are correct.

OOPS!

Forget my post :+

---

### Post by ajgreeny on 2006-05-07
Like a lot of people I have both desktops on my machine and they co-exist quite happily.  OK the menus can be a bit full, but you can always edit them yourself to put your needed progs at the top of the list, or even get rid of entries in menus that you never use.

I would not do that personally though, as you never know when you might just need something you've deleted the entry for.  OK you could always start it using the command line, but occasionally the command you need is less than obvious.  

Give it a try.  I much prefer KDE, but I have a new quite powerfull machine and it runs fast; on an older slower one maybe Gnome would be more appropriate.  I'm not sure if that last remark is still the case with the newer versions of Gnome, but it used to be so.

---

### Post by JLu on 2006-05-07
After installing kubuntu-desktop, your Gnome theme might be a bit borked, and the notification area in the top gnome-panel might not show everything it's supposed to show.  Removing the gtk2-engines-gtk-qt package fixes these problems (at least it worked for me and folks on this [related thread]("http://ubuntuforums.org/showthread.php?t=156053").

cheers, JL

---

### Post by aysiu on 2006-05-07
If you want to be able to remove KDE later **easily**, don't install it using *apt-get*.

As _jason mentioned, *kubuntu-desktop* and *ubuntu-desktop* are metapackages that just point to other packages. If you install those pointers with *apt-get*, you also install the packages they point to. If, however, you later decide to unistall the pointer, only the pointer itself (and not the packages it points to) will be removed.

It's better to use *aptitude*, which will remember what packages came along with the pointer: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` Later, if you want to remove KDE ```
sudo aptitude remove kubuntu-desktop
```

---

