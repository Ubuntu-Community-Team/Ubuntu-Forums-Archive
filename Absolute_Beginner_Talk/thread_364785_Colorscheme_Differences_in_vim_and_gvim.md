---
title: "Colorscheme Differences in vim and gvim"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by mepaco on 2007-02-18
Just wondering why color schemes aren't the same in vim and gvim.  For instance, I use the desert color scheme in gvim on my Windows box.  In Ubuntu (Edgy) the desert color scheme in gvim is exactly the same (gray background and muted colors).  However, when running vim through the terminal the background stays white and the colors are different.  Is this a limitation of the terminal or is there a setting I need to alter to make them look the same?

Thanks,
Paco

---

### Post by po0f on 2007-02-18
mepaco,

Do you have the colorscheme saved in ~/.vimrc or ~/.gvimrc?  I have it set in ~/.vimrc and it works for both.  The colors are a little off in the terminal, but it's basically the same.

---

### Post by mepaco on 2007-02-18
I don't have the colorscheme set in my vimrc file yet.  I was setting it after I opened up the program.  I don't know why but it is really off, especially the background (white vs dark gray).  I thought it worked correctly on my old Ubuntu install (Dapper) so I'm glad to hear it does work for you.  It gives me hope that I just need to tweak something.

-Paco

---

### Post by po0f on 2007-02-18
mepaco,

Just add something like the following to ~/.vimrc:

```
[FONT="Courier New"]" Set the color scheme
colorscheme desert[/FONT]
```

Works for me.  :)

---

### Post by eddin on 2008-01-07
A little late, but maybe this would be helpful to someone in the future.

The link below gives the reason why colors appear differently on the terminal (vim) and on gvim. The terminal is restricted to 8 background and 16 foreground color, while the gvim has 16 mil for each of background and foreground.


[http://groups.google.com/group/vim_use/browse_thread/thread/a325038a58ec9a9e](http://groups.google.com/group/vim_use/browse_thread/thread/a325038a58ec9a9e)

---

