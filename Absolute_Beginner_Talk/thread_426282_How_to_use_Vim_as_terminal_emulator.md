---
title: "How to use Vim as terminal emulator?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-28
Hello, I'd like to use Vim as my default terminal emulator, instead of GNOME terminal. I don't have anything again GNOME terminal, but I'd prefer Vim. Has anyone an idea how can I do that?

---

### Post by MRiGnS on 2007-04-28
vim isn't a terminal emulator oO

---

### Post by taurus on 2007-04-28
Vim is a text editor.

---

### Post by O-pos on 2007-04-28
is it not possible to use Vim at least as a skin for terminal? or what other terminal emulators exist?

---

### Post by MRiGnS on 2007-04-28
vim is just an application you can run in a terminal. it has no "skin".

other terminal emulators are for example aterm or xterm.

but could you please specify what do you ment with skin and further more what you don't like about gnome-terminal.

so we can fugure out how to help you.

---

### Post by taurus on 2007-04-28
I think you are a little confuse what vim is.

[http://en.wikipedia.org/wiki/Vim_(text_editor)](http://en.wikipedia.org/wiki/Vim_(text_editor))

---

### Post by Seisen on 2007-04-28
You can use eterm, xterm, instead of the gnome terminal. You should be able to find them in Synaptic.

---

### Post by O-pos on 2007-04-28
I work with a statistical program which has no gui and runs in terminal. For that statistical program (R) it's recommended to use emacs or vim to use most of it's power. I know that article about Vim in wikipedia, I saw it. I'd like my terminal to look not as a bunch of black letters, but more professional like Vim in this picture
[http://upload.wikimedia.org/wikipedia/en/2/28/Vim.png](http://upload.wikimedia.org/wikipedia/en/2/28/Vim.png)

and also I need lots text editing features, shortcuts etc..

also, when I work with mplayer, the same-colored whole text terminal is not so useful as color-coded.

If GNOME terminal has everything above mentioned then I'd stick with it, otherwise I'd need something as an alternative.

---

### Post by taurus on 2007-04-28
You need gvim then.

```
sudo aptitude update
sudo aptitude install vim-full gvim
```

---

### Post by O-pos on 2007-04-28
Thanks. After I install gvim then will it replace Gnome terminal by default, or are there other procedural steps which I should undertake after installation to use it as a terminal?

---

### Post by taurus on 2007-04-28
You just run it by looking for it in the Applications menu.  It will have it open window like the screenshot that you've included.

---

### Post by MRiGnS on 2007-04-28
> **O-pos said:**
> Thanks. After I install gvim then will it replace Gnome terminal by default, or are there other procedural steps which I should undertake after installation to use it as a terminal?

you can't replace gnome-terminal with gvim because gnome-terminal is an terminal emulator and gvim is a text editor.

it's just like you can't replace your washing machine with a flat to wash your clothes.

---

### Post by O-pos on 2007-04-29
OK, I see.

I've installed Gvim and I'm trying to make my statistical program run but I don't know how. In terminal I have to type R and there it starts. in Gvim typung R-s didn't help much :) I think I first have to start "shell" somehow and  probably then it should work.. Any ideas how can I do that?

---

### Post by MRiGnS on 2007-04-29
You can't run programs within vim, it's just not possible as vim is just a text editor.

##Du kannst vim/emacs nicht als ersatz für einen Terminal benutzen. Es sind Texteditoren. Es ist schlicht unmöglich.
    Du kannst keine Programme damit starten, du kannst keine Befehle aufrufen, nichts. Du kannst nur Text schreiben, diesen speichern usw.

---

### Post by ofek on 2007-04-29
Lets start by telling us which statistic program u use so we can understand what are u trying to do.

---

### Post by AaronMT on 2007-04-29
Think of GVIM/VIM as notepad you can not run a program in notepad. It's a text editor.

---

### Post by O-pos on 2007-04-29
:) Danke :)

I have  R: A language and environment for  statistical computing

I have seen myself running it in emacs. So at worse I could go to this person and ask how he did that.

In wikipedia they also say that it can be combined with text editor. And it's true, because so it's script language is more powerful. Here's the link:
[http://en.wikipedia.org/wiki/R_programming_language#Productivity_tools](http://en.wikipedia.org/wiki/R_programming_language#Productivity_tools)

---

### Post by twisted_steel on 2007-04-29
Is this what you are looking for?

[http://www.uft.uni-bremen.de/chemie/ranke/?page=vim_R_linux](http://www.uft.uni-bremen.de/chemie/ranke/?page=vim_R_linux)
[http://www.vim.org/scripts/script.php?script_id=1048](http://www.vim.org/scripts/script.php?script_id=1048)

It's a plugin for vim that allows you to edit the R files in one window, and send them to the R program in a terminal.

---

### Post by O-pos on 2007-04-29
yes, it seems to be that, thans :)

---

