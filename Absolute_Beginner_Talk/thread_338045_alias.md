---
title: "alias"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by hnaamyilkemku on 2007-01-13
when i enter certain commands into the terminal, i want them to be replaced by other, predefined commands. for instance, when i type "emacs" into the terminal, i want that command to be processed as "emacs -bg blue". how do i set this up in ubuntu? at my old lab each home dir had a file called .login that stored these aliases. here's an excerpt:

```

alias lock6 xlock -timeout 1 -mode swirl -timeelapsed -fg lightblue
alias lock xlock -mode swarm -batchcount 500
alias up cd ..
alias l ls
alias bye logout
```

thanks in advance!

---

### Post by taurus on 2007-01-13
Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```
Add the following lines to the end of it.

```

alias lock6="xlock -timeout 1 -mode swirl -timeelapsed -fg lightblue"
alias lock="xlock -mode swarm -batchcount 500"
alias up="cd .."
alias l="ls"
alias bye="logout"

```
Then, either log out and back in or run

```
source ~/.bashrc
```

---

### Post by po0f on 2007-01-13
hnaamyilkemku,

Put them in a file called ~/.bash_aliases.  Declare them like so:
```
[FONT="Courier New"]alias emacs='emacs -bg blue'[/FONT]
```
Now open up ~/.bashrc in your favorite text editor and add the following:
```
[FONT="Courier New"]if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi[/FONT]
```
There might be something along those lines already in there; if it's commented (lines begin with '#'), uncomment them.

---

