---
title: "Bash Aliases - open program in background"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by joesmoe10 on 2008-03-25
Hey all,

All I want to do is to type: 
> em filename.txt
and have emacs open in the background with filename.txt

alias em='emacs \!$1 &'

Here's what I've tried, but I get 
"bash: filename.txt: command not found"
Thanks for the help

---

### Post by glennric on 2008-03-25
Aliases can not do what you are asking.  See the man page for bash.  It is possible to do what you want with a shell function.  Again see the man page for bash.

---

### Post by fedex1993 on 2008-03-25
okay what you are going to do is use this command for an alias just add it to your .bashrc
alias em='emacs --file /location/to/file'

---

### Post by glennric on 2008-03-25
> **fedex1993 said:**
> okay what you are going to do is use this command for an alias just add it to your .bashrc
alias em='emacs --file /location/to/file'

If I am not mistaken he wants to be able to type
```
em filename.txt
```
to open a file that is specified at runtime.  That is what the $1 is for.  The problem is that aliases do not have parameters.  This can't be done with an alias as I said.

---

### Post by glennric on 2008-03-25
If you want this to work add the following to the file ~/.bashrc
```
em () {
  emacs $1 &
}
```
Then restart the terminal for it to take effect.  This will do what I think you are trying to do.  Type
```
em filename.txt
```
and emacs should open the file filename.txt in the background.

---

### Post by joesmoe10 on 2008-03-26
awesome, exactly what I wanted.  Thanks for the help

---

