---
title: "how do i install cursor skin"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-16
i got cursor skins.. but i dont know how to put it in.. can anyone help me ?

---

### Post by yabbadabbadont on 2007-03-16
sudo apt-get install gcursor

Then there should be a cursor option in System->Preferences that will let you select the theme you want.  (Assuming that you are using Gnome)

---

### Post by K.Mandla on 2007-03-16
I think there's a [gcursor]("http://packages.ubuntu.com/edgy/gnome/gcursor") utility that should let you pick a cursor theme. If you're not using Gnome, decompress it into a directory at ~/.icons and set it in a file called ~/.Xdefaults with something like this.

```
Xcursor.theme:name_of_the_folder_the_cursor_theme_decompressed_to
```

Edit: Darn. Yabba beat me to it. :evil:

---

### Post by yabbadabbadont on 2007-03-16
> **K.Mandla said:**
> Edit: Darn. Yabba beat me to it. :evil:

A pleasant change.  I'm used to being the bottom rail.  :lol:

---

### Post by HunkieChan on 2007-03-16
> **K.Mandla said:**
> I think there's a [gcursor]("http://packages.ubuntu.com/edgy/gnome/gcursor") utility that should let you pick a cursor theme. If you're not using Gnome, decompress it into a directory at ~/.icons and set it in a file called ~/.Xdefaults with something like this.

```
Xcursor.theme:name_of_the_folder_the_cursor_theme_decompressed_to
```

Edit: Darn. Yabba beat me to it. :evil:

thanks alot guys

---

### Post by HunkieChan on 2007-03-16
> **yabbadabbadont said:**
> A pleasant change.  I'm used to being the bottom rail.  :lol:

i got gcursor .. thanks a lot guys.. i hope this might work.. since you guys here can you help with something else. .. when i log in.. amarok, gaim, a folder and session loads automatically.. how can i disable to not load ?.. thanks

---

### Post by K.Mandla on 2007-03-16
:-k I think you might check the sessions dialogue ... I think that's where the startup programs are listed. I haven't used Gnome in a while, though.

---

### Post by HunkieChan on 2007-03-17
> **K.Mandla said:**
> :-k I think you might check the sessions dialogue ... I think that's where the startup programs are listed. I haven't used Gnome in a while, though.

it is is there.. i remove em and click apply but it still shows up.. what should i do ?

---

### Post by yabbadabbadont on 2007-03-18
> **HunkieChan said:**
> it is is there.. i remove em and click apply but it still shows up.. what should i do ?

Use Fluxbox?   :D

Check the last tab and if they are listed there, select them and either remove them, or disable them.  (whichever one it will let you do)

---

### Post by HunkieChan on 2007-03-18
> **yabbadabbadont said:**
> Use Fluxbox?   :D

Check the last tab and if they are listed there, select them and either remove them, or disable them.  (whichever one it will let you do)

how do i install it.. i tried to install it from synaptic.. but it doesnt start up
what should id o ?

---

### Post by HunkieChan on 2007-03-18
EDIT: double post

---

### Post by Andy0 on 2008-05-11
much later ...

For 8.04, gcursor didn't work for me. 

Instead while having system<preferences<appearance open, I just dragged my compressed cursor set into the theme window :)

---

