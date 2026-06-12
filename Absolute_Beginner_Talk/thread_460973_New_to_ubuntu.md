---
title: "New to ubuntu"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Mobjerkn on 2007-06-01
Hi, I've just installed a Ubuntu OS on my laptop. I can't do a ll to browse my filesystem and have to write ls -l to list files. Anyone know how to get around this (just a bit anoying)
Regards

---

### Post by shearn89 on 2007-06-01
does just "ls" work?

---

### Post by Mobjerkn on 2007-06-01
yes ls and ls -l but I'm lazy and wanna do a ll ....

---

### Post by Outrunner on 2007-06-01
Excuse my ignorance but what exactly does the command 'll' do? Or at least, what is it supposed to do?

EDIT: Ahh, I see now, it doesn't do anything by itself , you just wanted to type ll instead of ls because you felt like it. Interesting. :rolleyes:

---

### Post by EndPerform on 2007-06-01
Add this line to your .bashrc:

```
alias ll='ls -l'
```

Like so:

```

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    alias ll='ls -l'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

```

And that will get you what you need.

---

### Post by Mobjerkn on 2007-06-01
is this a file I will have to edit or just run the command in the shell?
Thanks for update so far....
Mo

---

### Post by Mobjerkn on 2007-06-01
sorry for the last update didn't read the complete post. Did find the file and is now editing the file with the preferred settings for me. Thanks for great help.
Regards

---

### Post by gerscht on 2007-06-01
when you put the above command in .bashrc it will be available when you open a new terminal window (as the file is executed at the beginning)

---

### Post by Carlos Santiago on 2007-06-01
EndPerform is right!
'll' is a very usual alias, but it is not a POSIX command. 
That means it is not Unix (or Linux) standard.

If you want to use, you have to add it to your .bashrc

You can use the EndPerform's version:
```
alias ll='ls -l'
```

but I prefer this:
```
alias ll='ls -Fo --color --group-directories-first'
```

---

### Post by hillbilly on 2007-06-01
I usually keep a .bash_aliases file in my home directory which contains all the aliases I require. And in .bashrc i add the following code commands:

> if [ -f ~/.bash_aliases ]; then
   . ~/.bash_aliases
fi

This way its easy for me to maintain my aliases. In case I need to update my aliases I just do this from the command line:

> echo alias *command*=*command_with_ options_ e.t.c.* >> ~/.bash_aliases

---

