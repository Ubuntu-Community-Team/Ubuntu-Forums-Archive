---
title: "quick vim question"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Alberio on 2008-02-18
hey,

I'd like to make it so that tab will act to switch between modes. 

it's just that escape is getting annoying to use ESC to go back to command mode. I'd rather to use TAB

I've got autoindent on and only working in Lisp and C++... so tab isn't doing much right now.

Thanks,
        Alberio

---

### Post by stchman on 2008-02-18
Use Gedit.

---

### Post by Joeb454 on 2008-02-18
I don't think that's the solution that the OP was after.

VIM has many uses (such as being available on all *nix machines) Though I'm not much of a vi/vim user so I can't really give a proper answer, sorry.

---

### Post by stroyan on 2008-02-18
You can get that effect by adding these lines to ~/.vimrc -
```
"stop insert mode with tab
map!<C-I> <C-[>
"start insert mode with tab
map<C-I> i 
```

But that binding seems really strange to me. :shock:

---

### Post by Alberio on 2008-02-18
Thank you stroyan

yeah, it might seem weird to some, but the ESC key is a stretch, and when Im' working on the laptop that key is particularly tiny. I don't really need to use tab, autoindent takes care of that for me. Thanks again

stchman:

no. if anything I'd use Kate, I use vim for remote work, and sometimes when I feel like using a CLI

---

