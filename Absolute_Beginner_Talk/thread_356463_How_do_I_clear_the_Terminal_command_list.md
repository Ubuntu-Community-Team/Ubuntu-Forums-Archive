---
title: "How do I clear the Terminal command list?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-02-08
I'm setting up Ubuntu for my parents so I want to clear the command list in Terminal when you click the up/down arrow keys.  So that they don't run some command they don't understand and complicate stuff when I instruct them by phone in the future.

---

### Post by compmodder26 on 2007-02-08
If you want to do it manually use the command "history -c"

If you don't want the history to ever show up again.  Place the line "HISTFILESIZE=0" in their .bashrc file (in the home directory).

edit:  The line should read "**export** HISTFILESIZE=0"

---

### Post by tkjacobsen on 2007-02-08
rm .bash_history

---

### Post by jingo811 on 2007-02-08
tnx I did 
> history -c

---

### Post by ardchoille42 on 2007-02-08
A history of your terminal commands is kept in ~/.bash_history. You can do one of two things here:

```

echo "" > ~/.bash_history

```
This overwrites everything in ~/.bash_history with the text contained in "" (eg. it will blank the file).

OR

```

rm ~/.bash_history

```
This removes the file altogether.

Either one will yield the same result. I use 'rm ~/.bash_history' in a daily cronjob that deletes junk before making a backup of my $HOME.

Using 'history -c' will temporarily remove the ability to use the arrow keys to browse previous history (until new history is added), but it won't clear ~/.bash_history, someone can still come along and cat ~/.bash_history and see what you've done.

---

### Post by jingo811 on 2007-02-10
but if you remove the file
```
rm ~/.bash_history
```
do you need to recreate it later on when you want to access your newly used commands more quickly with the arrow keys?

---

### Post by tkjacobsen on 2007-02-11
> **jingo811 said:**
> but if you remove the file
```
rm ~/.bash_history
```
do you need to recreate it later on when you want to access your newly used commands more quickly with the arrow keys?

No, bash will create a new one next time you use the terminal.

---

### Post by jingo811 on 2007-02-11
tnx

---

### Post by alanhaggai on 2007-02-11
That was a new piece of info. Thank you friends. :)

---

### Post by compmodder26 on 2007-02-12
You can also use any variety of the answers above to clear the history when the user logs in.  This will allow them to keep their history for the duration of their session.

For my instructions, in ~/.bashrc place the following lines:
```
export HISTFILESIZE=0
export HISTFILESIZE=30
```

That will allow up to 30 commands to be remembered for the session.

For the other advice, in ~/.bashrc, place the line:

```
rm ~/.bash_history
```

Both yield the same results.

---

