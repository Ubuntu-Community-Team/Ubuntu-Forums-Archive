---
title: "vi annoys me"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by jombeewoof on 2007-07-13
Whenever I use vi, on any of my systems with any debian based distro I have problems.
I can't use the arrow keys.
using any arrow key results in strange characters on the screen adding lines and it just plain annoys the crap out of me.
If I recompile, I assume it will use the same settings that are setup now, how do I recompile it to act more like vi in any other distro I've used that isn't debian based.

EDIT
Only happens in insert mode

I added 

set esckeys 

to .vimrc in my home directory

---

### Post by sab0403 on 2007-07-13
one word:

emacs.

---

### Post by adampyre on 2007-07-13
I'm newish so therefore I am ignorant, but I've been using nano...... are vi and nano the same thing? I have an easier time with nano myself...

---

### Post by FleetAdmiral74 on 2007-07-13
I am a noob to, but I believe they do the same thing, as in they are both command line text editors, just competing programs. people have their preferences over one or the other, but they are pretty equal.

---

### Post by girishv on 2007-07-13
Hi,

I never faced this prob on my ubuntu. Earlier when working on redhat connecting to other terminals through telnet used to give me these problems though.
Can you try using vim instead of vi (though vi is just a link to vim)
and setting nocompatible in your vimrc

girish

---

### Post by expatCM on 2007-07-13
consider listening to episode 69 at this link
[http://www.linuxreality.com/](http://www.linuxreality.com/)

---

### Post by yabbadabbadont on 2007-07-13
Learn to properly use vi (vim).  :D  You never need to remove your hands from the home row of the keyboard that way.  ;)

Hint:  

h = move left one character
j = move down one line
k = move up one line
l = move right one character

It's a pain to learn, but very powerfull once you do.  If you just want a basic Notepad type editor for the terminal or command line, then use nano.

---

### Post by Kerdenay on 2007-08-18
You are using **vim-tiny** (a default in Ubuntu, I think), while you want to use **vim**. Install one, uninstall the other and you should be just fine :)

---

### Post by Lord Illidan on 2007-08-18
Yes, this command will do the trick.

```
sudo aptitude install vim-full
```


Before suggesting other editors, first try and solve his problem.

---

