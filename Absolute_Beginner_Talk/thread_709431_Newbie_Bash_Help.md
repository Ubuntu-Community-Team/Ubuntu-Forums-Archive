---
title: "Newbie Bash Help"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by FISHERMAN on 2008-02-27
I've put this in bash profile:

alias bc='bc -l'

So that bc autmatically loads the floating library.
But when I type in bc it doens't automatically load the floating library.
What I am doing wrong?
PS. when I name the alias to something that isn't in my PATH it works.

---

### Post by taurus on 2008-02-27
Bash profile you mean ~/.bashrc?  And have you logged out and back in again or at least rehash it with

```
source ~/.bashrc
```
after you modified ~/.bashrc?

---

### Post by Crooksey on 2008-02-27
is it in ~/.bashrc ?

---

### Post by Darkdelusions on 2008-02-27
Yes it would be locate in ~/.bashrc

---

### Post by FISHERMAN on 2008-02-28
OK, I've managed to get alias bc='bc -l' working by puting it in the bashrc but the alias ls='ls- F' still refuses to function(yes, i've also put it in the bashrc) Any help on that one

---

### Post by taurus on 2008-02-28
Try

```
alias ls="ls -F"
```
Be careful where you put the empty space!

---

### Post by Oldsoldier2003 on 2008-02-28
> **taurus said:**
> Try

```
alias ls="ls -F"
```
Be careful where you put the empty space!
QFE

FISHERMAN:
A good way way to make sure you type things correctly when editing your  ~/.bashrc or any other script is to use the middle mouse button trick :)  if you aren't familiar with this I'll explain.
 
1> Open two terminals. type your command in the first terminal. this is your "sanity check" to make sure you have the syntax correct.
2> in the first terminal highlight the command then switch to the second terminal
3>click the middle mouse button and the text will be pasted in the second terminal.


this trick can be used anywhere in linux, because the currently selected text is available for paste. beware that currently selected is exactly that- if you highlight something else in any other app it will become the new middle button paste. If you want to learn more just search for clipboard and read about the different aspects of the linux clipboard.. primary etc

---

