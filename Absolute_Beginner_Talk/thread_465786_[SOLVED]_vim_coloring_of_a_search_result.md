---
title: "[SOLVED] vim coloring of a search result"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by sundol on 2007-06-06
When I press * on a word of vim, all same word are colored as brown in Fedora but not in ubuntu 7.04

How can I do same thing in Ubuntu?

---

### Post by hardyn on 2007-06-06
[http://www.cyberciti.biz/faq/turn-on-or-off-color-syntax-highlighting-in-vi-or-vim/](http://www.cyberciti.biz/faq/turn-on-or-off-color-syntax-highlighting-in-vi-or-vim/)

isn't google wonderful

---

### Post by Crafty Kisses on 2007-06-06
> **hardyn said:**
> [http://www.cyberciti.biz/faq/turn-on-or-off-color-syntax-highlighting-in-vi-or-vim/](http://www.cyberciti.biz/faq/turn-on-or-off-color-syntax-highlighting-in-vi-or-vim/)

isn't google wonderful

:p

---

### Post by Skrynesaver on 2007-06-06
True google is wonderful, however you have to ask it the right question, in this instance rather than syntax highlighting you should have been searching for search highlighting ;)
```
[Esc]:set hlsearch
``` should do it in the present buffer.  If you want this to be the default add the line "set hlsearch"  to your ~/.exrc.

---

### Post by hardyn on 2007-06-06
Search HL is activated with text HL.  and as ubuntu does NO highlighing out of the box... i assumed that he may want some color too...

---

### Post by Skrynesaver on 2007-06-06
Actually you can have search highlighting independently of syntax highlighting in vim, but yes anyone who wants search highlighting will probably want to turn on syntax highlighting also

---

### Post by sundol on 2007-06-06
> **Skrynesaver said:**
> True google is wonderful, however you have to ask it the right question, in this instance rather than syntax highlighting you should have been searching for search highlighting ;)
```
[Esc]:set hlsearch
``` should do it in the present buffer.  If you want this to be the default add the line "set hlsearch"  to your ~/.exrc.

Thank you. This is exactly what I wanted.
I didn't know how to turn on search highlighting and the term search highlighting itself, although I knew those for syntax coloring. Weird ;) This was probably  why my googling failed. 

I hope these option will be included, as a default, in files such as vim.python or something like that in Ubuntu :)

Thank you

---

