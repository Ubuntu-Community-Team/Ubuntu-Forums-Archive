---
title: "vim background color setting no effect"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Acyong on 2006-11-04
Under Ubuntu Linux Distro, in /etc/vim directory, to modify vimrc file by un-commenting the line shown as below:
```
set background=dark
```
but, it doesn't tack effect. the background is still white.
How to set the background of vim to black color? and the font color to white?:confused: 

Thanks.

---

### Post by David_T on 2006-11-04
If what you want to work with a black background in vim, here are your options:

If you are using the console version of vim, you can either make your console background black, or choose a colorscheme that has a black background.  For example, try "set colorscheme=torte".  You could put this in your ~/.vimrc.

If you are using gvim, you can invoke it as gvim -rv (for reverse video).  This appears to only work if you do not have a colorscheme set in your ~/.vimrc.

---

