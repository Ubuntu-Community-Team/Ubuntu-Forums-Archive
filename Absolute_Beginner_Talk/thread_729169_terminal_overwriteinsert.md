---
title: "terminal: overwrite/insert"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by stainless_steel on 2008-03-19
i love using the terminal, but how do i toggle between insert and overwrite mode? the "insert" key works in all other apps, but not the terminal.

---

### Post by (((X))) on 2008-03-19
Isn't it Shift+Insert

Rightclick and paste works best imo

---

### Post by Nythain on 2008-03-19
not all terminals support right click and paste, though you are correct on
shift+insert being the shortcut for pasting... in some terminals, to copy all you have to do is highlight... and as for "insert" well, i never insert things short of actually typing them :)

---

### Post by glennric on 2008-03-19
> **(((X))) said:**
> Isn't it Shift+Insert

Rightclick and paste works best imo

Shift+Insert pastes from the clipboard.  That is not what he is asking.  I am not sure how to do that in a terminal.

---

### Post by (((X))) on 2008-03-19
Yes, Rightclick+pastye won't paste to xterm

---

### Post by glennric on 2008-03-19
> **(((X))) said:**
> Yes, Rightclick+pastye won't paste to xterm

Can any of you read?  He is asking about toggling insert/overwrite mode with the insert key, not cutting and pasting.  By the way, right click paste works in gnome-terminal.  This is the default terminal in Ubuntu.

---

### Post by Nythain on 2008-03-19
ok, so instead of just flaming us for at least trying to help, why dont you post a flippin answer... we were at least on topic, the wrong topic, but on topic none the less... what good does criticizing us do for the original poster...

and now back to the matter at hand... im not sure if this helps, found with a bit of googling (i never really switch between insert and overwrite mode myself) but your answer may lie in here somehwre, then again it may not... but at least im trying

[http://www.calmar.ws/linux/man-bash.html](http://www.calmar.ws/linux/man-bash.html)

---

### Post by glennric on 2008-03-19
I have been searching for a way to do this, and as of yet have had no luck.  If you type "bind -P" in the terminal you can see the key bindings and that overwrite-mode is not bound to anything.  I am working on figuring out how to bind that to the insert key.

---

### Post by glennric on 2008-03-19
Ok, I have it.  Edit/Create the file .inputrc in your home directory containing the lines
```
# Toggle insert/overwrite mode
$if mode=emacs
"[2~": overwrite-mode
$endif
```
Note that the stuff inside the quotes must be typed by hitting "Ctrl-v" then "insert" if you are using vim and will look like "^[[2~" in vim.  If you are using gedit or something else try cutting and pasting.  Then restart the terminal and the insert key will work.

Edit:  I attached the file.  Just gunzip it in your home directory.

---

### Post by stainless_steel on 2008-03-20
thanks! you rule, it works great. it was a pain to keep typing something in and then deleting the offending character. (usually a case sensitive issure /.trash > /.Trash
i tried just copying and pasting the code you displayed and it didnt work. when i used your file i noticed that odd character. what is it?

BTW, i appreciate ALL the help. no need for harsh words. 
(ctrl+shift+v is how i  past a block of text into the terminal.) i wonder if  the middle mouse button will work? (trying it now)...      IT DOES! cool.

---

### Post by stainless_steel on 2008-03-30
bump

---

