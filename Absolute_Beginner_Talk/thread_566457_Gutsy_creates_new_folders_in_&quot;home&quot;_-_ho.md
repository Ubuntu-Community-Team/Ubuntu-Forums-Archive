---
title: "Gutsy creates new folders in &quot;/home&quot; - how do I reorganise to link my default folders"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by SabrinalovesUbun2 on 2007-10-03
Hi
I just upgraded Feisty to Gutsy

gksu "update-manager -c -d"

Gutsy creates new default folders **(Documents, Music, Pictures, Videos**) also seen in the **"Places"** menu. [I](and maybe a bug: Desktop shows up twice under Places, should be Template I guess)
[/I]
**Question:**  I already have my own "Documents, Music, Pictures, Videos folder" in home but organized inside another folder, how can I link the new places menu shortcuts to my Documents, Music, Pictures, Videos folders?

and can I delete the other Documents, Music, Pictures, Videos folders which gutsy created? 

or whats the best way to use this new feature?

---

### Post by Sunforge on 2007-10-03
Editing the places menu appears to work like this:

sudo gedit ~/.gtk-bookmarks

The entries in this file map directly to your home folder. All you do by deleting an entry in this file is delete the shortcut so you have to manually remove the folder in your home folder afterwards.

You can put what you like in the gtk-bookmarks file as far as I can tell and it'll show up, although I did find listing too many entries made for some weirdness.

Remember to make a copy of the file before you do anything.

---

### Post by master_kernel on 2007-10-03
You could also use
```
ln -s OLDFOLDER NEWFOLDER
```

That creates a symbolic link.

---

