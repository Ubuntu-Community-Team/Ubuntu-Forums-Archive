---
title: "Changing Indent Length In Vim"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by chessercizes on 2007-07-04
Hey guys.

 I had a question about VIM. Is it possible to change the indent length? Like recently i started getting into programming, and vim auto-indents after i start an if statement, but is it possible to change the length it goes?

I looked in the /etc/vim/vimrc file, but couldn't find anything to change it.

Thanks.

-parth

---

### Post by Golyadkin on 2007-07-04
you can use the sw setting:
> 
:set sw=4
 
sets the shift width (indentation depth) to 4 spaces.

---

### Post by nitro_n2o on 2007-07-04
> **Golyadkin said:**
> you can use the sw setting:
 
sets the shift width (indentation depth) to 4 spaces.

You need to put this in ur .vimrc file or /etc/vim/vimrc 
I'd highly recommend that you have your own .vimrc file in your home directory instead of changing settings globally

---

### Post by tpg on 2007-07-04
You might also want to
```
:set tabstop=4
```

---

### Post by chessercizes on 2007-07-04
Yay. This was absolutely perfect. Thank you guys!

---

### Post by Golyadkin on 2007-07-05
You are welcome!

---

