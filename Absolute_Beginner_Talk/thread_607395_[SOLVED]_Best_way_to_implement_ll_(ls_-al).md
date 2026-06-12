---
title: "[SOLVED] Best way to implement ll (ls -al) ?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-11-08
I have always liked to use the 

ll

command in unix, which is really the same as

ls -al


Ubuntu doesn't have ll, so I edited/created a file called ll, in which I placed the ls -al command. I then chmodded this for execute and copied it to /usr/local/bin (on the path)

This all works, except the directory listing that results, loses the colours that you normally see when you use ls -al directly in a terminal.

Any ideas on how to fix this?

---

### Post by Dr Small on 2007-11-08
I see this in .bashrc:
```
alias ls='ls --color=auto'
```

Would that help any?

---

### Post by llamakc on 2007-11-08
Just add the alias to ~/.bash_aliases like this:

alias ll="ls -al"

and then run

source ~/.bash_aliases

---

### Post by taurus on 2007-11-08
Why not edit your ~/.bashrc

Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```
and add this line to the end of it.

```
alias ll="ls -al"
```
Save it.  Then, source it with

```
source ~/.bashrc
```
Now, run **ll** from a terminal and see what happens.

---

### Post by ubnewbie2 on 2007-11-08
Oops, solved this already.   There's a bunch of alias's all ready to be uncommented in the user's  ~/.bashrc file.  That works with colour, and is much more elegant :-)

---

### Post by ubnewbie2 on 2007-11-08
oops again, I see lot's of people have helped me already.  Thanks everyone

---

