---
title: "How do I save with Vim in the shell?"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by Hygelac on 2005-12-25
This is just a basic question.  I have to edit a file with Vim in the shell (I cannot run graphically until I do so), but don't know how to save it!  So, how do I do so? :???:

---

### Post by ubuntuuser on 2005-12-25
Press Esc to make sure you're in normal mode,
Shift+Q
wq

That's it.

---

### Post by Hygelac on 2005-12-25
Thanks; it is working perfectly.  :cool:

---

### Post by bscbrit on 2005-12-26
VIM commands:

[http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)

Start to learn vim or emacs today - one day, you will be glad that you did!

---

### Post by briancurtin on 2005-12-26
"wq" is good to write then quit, but if you just want to save while you are working on something, just do a plan "w" in normal mode

---

### Post by jocke1s on 2005-12-26
Why use shift+Q?

I simply do : to get into ex mode. Are there anything I am missing out on when I don't use shift+Q. 

I tried it and it says I need to write "visual" to go back to visual mode.

When I simply type : I can go back with "backspace"

I usually save my file with

:wq
:w
:w!
:w file.txt
:'a,.w partoffile.txt

or something.

Regards
Joakim

---

### Post by odin on 2005-12-26
I just press Esc and then type

:w (just to save)
:x  (to save and exit.this is the same as typing :wq)

---

### Post by Hygelac on 2005-12-26
I thank you all for the additional information. :)

---

### Post by bagel on 2005-12-26
I use:
<Esc>
:x

(done) :)

Edit.. oh.. that was the angry smile in the post above... 
:x means ```
:x
```

---

