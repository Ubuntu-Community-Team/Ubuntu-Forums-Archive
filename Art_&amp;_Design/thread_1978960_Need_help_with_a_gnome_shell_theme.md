---
title: "Need help with a gnome shell theme"
date: 2012-05-12
forum: Art &amp; Design
---

### Post by dbbolton on 2012-05-12
I'm using Faience, and for some reason I'm getting red text in the window thumbnail view: 
[http://i.imgur.com/EvGll.png](http://i.imgur.com/EvGll.png)

I've removed and reinstalled the theme twice, and I can't figure out where this red text is coming from.

Doing 
```
grep -in 'ff0000' ~/.themes/Faience/gnome-shell/*
```
Turned up nothing. I also tried opening an uncompressed screenshot into Gimp and choosing the color of an un-aliased pixel of the text, then searching for the color, and still nothing.

Can someone tell me what this property is called, and whether there may be a cache of the theme somewhere other than where I'm looking?

---

### Post by ckop64 on 2012-05-14
Check the link, first comment. The behaviour is caused by an extension.

[http://gnome-look.org/content/show.php?content=144815](http://gnome-look.org/content/show.php?content=144815)

---

### Post by dbbolton on 2012-05-17
Hmm, I don't have any window placement extension.

---

### Post by ubiquitin.jf on 2012-05-18
The gnome-shell 3.4 update broke a few things in themes. The #gnome-shell group on deviantArt is a great source of information on how to fix these things ([link]("http://gnome-shell.deviantart.com/journal/GNOME-3-4-Theme-Talk-294078943")) and maintains a list of themes available which are compatible with 3.4.

[EDIT] Looks like somebody has already unofficially updated the theme to work on 3.4 - [Enjoy!](http://erabong.deviantart.com/art/Faience-3-4-300563619)

---

