---
title: "Where is everything!?"
date: 2005-08-05
forum: Absolute Beginner Talk
---

### Post by Epyon on 2005-08-05
im used to Windows where it would just be C:\Programfiles\"whatever"

where are all the program folders here? like i have amule, and i downloaded some music, where is the folder that is housing them?

---

### Post by krusbjorn on 2005-08-05
Usually programs are installed in /usr.

But since you need root privilegies to write outside your home folder, you can be sure that your downloaded music is somewhere in /home/<username>/ if you didnt run amule as root. 

Edit: BTW, you can probably see where your downloaded files are, if you look into amule's preferences.

---

### Post by bored2k on 2005-08-05
[QUOTE=krusbjorn]Usually programs are installed in /usr.

But since you need root privilegies to write outside your home folder, you can be sure that your downloaded music is somewhere in /home/<username>/ if you didnt run amule as root.[/QUOTE]
 amule files are usually in $HOME/.amule/Incoming , or something like that.

---

### Post by Epyon on 2005-08-05
i think i did run as root, cause i did sudo -s -H if i remember correctly...

---

### Post by Epyon on 2005-08-05
kk, just found it! lol


another question is there a way to get gkrellm to run without using up a window slot on my bar?

---

### Post by krusbjorn on 2005-08-05
yeah, you can use a program called devilspie. However, it can be quite advanced if you are an "absolute beginner" ;)

There are a few threads here on the forum about it. Do a search :)

[QUOTE=Epyon]kk, just found it! lol


another question is there a way to get gkrellm to run without using up a window slot on my bar?[/QUOTE]

---

### Post by Epyon on 2005-08-05
i think i moved up from the low tier of absolute beginner to Beginner.

i finally got all my plugins and azeurus running today. i will look into this devilspie

---

### Post by Epyon on 2005-08-05
but where is the exectuable file for Totem or Mplayer?

---

### Post by krusbjorn on 2005-08-05
You probably dont need to know where they are, since there are "symbolic links" for them in your /usr/bin folder.  Try just typing "totem" or "gmplayer" in a terminal. 

[QUOTE=Epyon]but where is the exectuable file for Totem or Mplayer?[/QUOTE]

---

### Post by Ampersand on 2005-08-05
most executables are in /usr/bin, however you should be able to run everything from the Applications menu. If they don't appear there, you can run them from a terminal by typing the name of the program (in most cases, occasionally the executable name is shortened). You don't need to go to the folder to run them.

---

### Post by Epyon on 2005-08-05
thanks guys, im really loving Ubuntu, and moreover cause of the awesome ppl who are helping, THANKS EVERYONE!!!!!!

---

### Post by bored2k on 2005-08-05
[QUOTE=Ampersand]most executables are in /usr/bin, however you should be able to run everything from the Applications menu. If they don't appear there, you can run them from a terminal by typing the name of the program (in most cases, occasionally the executable name is shortened). You don't need to go to the folder to run them.[/QUOTE]
 And if you wan't to make your own shortcuts, make sure you get the SMEG Menu Editor . [http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor)

---

### Post by nic2 on 2005-08-06
Another alternative is the following two options (of which I prefer the latter)

[list]
[*]from the panel click on Applications > Run Application ...
[*]press alt + f2 keys
[/list]

Ps. relates to posts by Krusbjorn and Ampersand - great tip by Bored2k

---

