---
title: "vim and fonts"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by n.aggel on 2006-10-30
Hi, can anyone suggest a default font for using with vim.I recently migrated to ubuntu from windows where i Courier New with gVim[set guifont=Courier_New:h12:b:cGREEK].

Does anyone know a font set that looks like the one i used[it would be nice if it looked nice with torte colorscheme]?

Also the ubuntu-system default font[the one used with the console] is nice but i don't know its name.:???: 

I tried to use monospace font[the one used with gedit] and i noticed that writing:

	set guifont=Monospace:h12:b

in my vimrc file doesn't work!! But if write
	
	set guifont=Monospace

it works perfectly...(?!)](*,) .What am i doing wrong in the first case??

thanks in advance for your time,

N.A

---

### Post by tatimmer on 2006-10-30
I use vim in the gnome-terminal and you can set terminal fonts thru the main menu (system->fonts or something like that)

---

### Post by kaamos on 2006-10-30
> 
set guifont=Monospace:h12:b

in my vimrc file doesn't work!! But if write

set guifont=Monospace

it works perfectly...(?!) .What am i doing wrong in the first case??


Try "set guifont=bitstream\ vera\ sans\ mono\ 12"

---

### Post by n.aggel on 2006-10-30
> 
I use vim in the gnome-terminal and you can set terminal fonts thru the main menu (system->fonts or something like that)


unfortunatelly this approach doesn't work if someone uses gVim, it only works for vim...

---

### Post by n.aggel on 2006-10-30
> **kaamos said:**
> Try "set guifont=bitstream\ vera\ sans\ mono\ 12"

thanks, great font set, but again i try to make it bold, and it doesn't work...:(

i try:
set guifont=bitstream\ vera\ sans\ mono\ 12\ b and nothing...

do you know how can i make it bold???

thanks for your help:)

---

