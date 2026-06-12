---
title: "Location of .vimrc file?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by islander_810 on 2007-03-17
Can anyone tell me where the .vimrc file is located? I can't find it in my home folder

---

### Post by j.miller565 on 2007-03-17
That is a hidden folder in /home/   

to find it, go to the View tab and then you look down until you see Show Hidden Files

Now you can see the hidden files in your home directory. Now you should be able to find the .vimrc folder.


hope this helps

---

### Post by scxtt on 2007-03-17
i don't believe there is a default ~/.vimrc ... you can just create it ...

---

### Post by reclusivemonkey on 2007-03-17
If you go through vimtutor, there is a section which guides you through creating a default .vimrc which you can edit to your preferred settings.

---

### Post by islander_810 on 2007-03-17
Nope, no hidden file or folder named .vimrc or anything.

How do i create a default .vimrc file?

And does Vim 7.0 support syntax highlighting. Cos when i checked the version it shows the option as -syntax. Is it disabled by default?

---

### Post by scxtt on 2007-03-17
to create a .vimrc file, do:
 
vi ~/.vimrc
 
then add vi(m) commands to it, mine currently has:
[indent]set hlsearch
hi Search ctermfg=black ctermbg=white[/indent]
 
and as far as syntax highlighting, ubuntu uses "vim-tiny" by default - try installing "vim-full" ...

---

### Post by islander_810 on 2007-03-17
Thx, got it.

---

