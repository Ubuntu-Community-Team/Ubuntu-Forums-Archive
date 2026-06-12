---
title: "Where do Synaptic install?"
date: 2005-06-22
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-06-22
How do I know where synaptic install a program and/or what command the new application gets?

---

### Post by aamir on 2005-06-22
synaptic installs in the same place a deb file requests to be installed. 

the application should show up in your desktop menu, if you  are trying to run from command line then start typing the name of the application and hit tab, the system should fill in the rest or at least give you a list of possible matches

---

### Post by Trojan1313 on 2005-06-22
[QUOTE=aamir]synaptic installs in the same place a deb file requests to be installed. 

the application should show up in your desktop menu, if you  are trying to run from command line then start typing the name of the application and hit tab, the system should fill in the rest or at least give you a list of possible matches[/QUOTE]
 Well, it doesn't always show up there. =/ I've tried the tab-thingie, but the application I was looking for when making this thread (Genesis) won't show.

Is there no way of guessing through what kind of application it is? For example "Hmm, a game, that should be installed in blablabla/games or something like that"?

---

### Post by somuchfortheafter on 2005-06-22
try the search for files option....

---

### Post by SGC on 2005-06-22
You can add the debian menu which we show **all** the installed applications on you computer:

sudo apt-get install menu menu-xdg

Then relogin from you account.

---

### Post by Trojan1313 on 2005-06-22
[QUOTE=somuchfortheafter]try the search for files option....[/QUOTE]
I've seen it somewhere, but I don't know where. :P lol :P

---

### Post by somuchfortheafter on 2005-06-22
should be in places menu up top.....

---

### Post by Kyral on 2005-06-22
or use the locate command, but first you are going to have to create the database.

```
sudo slocate -u /
```

when that is done

```
sudo slocate <filename>
```

---

