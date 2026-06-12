---
title: "Shortening commands in terminal"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by puggers on 2006-07-12
How do I create new shortcuts for the terminal?

eg, each time i want to start utorrent via wine, have to type in ```
wine c:\utorrent.exe
```

How do I make it so I could simply type in 'UT' instead? I've seen it explained before, but i've searched the forum and couldn't find it. Also is it possible to start a number of programs using a single command?

Any help would be much appreciated!

-steve

---

### Post by siccness on 2006-07-12
Using alias, 

alias UT='wine c:\utorrent.exe'


Your second question, I'm unsure of. But I doubt it because if you load up something like firestarter from the terminal, it'll throw output into the terminal, and I don't think you can have two different outputs into one terminal. I could be wrong though.

---

### Post by someusernoob on 2006-07-12
In your /home dir there are 2 files you need to edit: .bashrc and .bash_aliases. To show them make Hidden Files visible (in nautilus: View > Show Hidden Files.

Open .bashrc and find this ( a little bit above the end of the file):
```

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

```

Remove the # and make it look like this:
```

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

After that save the file, close it, and open .bash_aliases.

You can put in commands like siccness said:
```

alias UT='wine c:\utorrent.exe'

```
where UT is the thing you type in the terminal and 'wine c:\utorrent.exe' is the command attached to it.

When you want 2 (or more) programs started up with one command enter it like this:
```

alias 2programs='nautilus && firefox'

```
This opens nautilus and firefox at the same time. I named the alias 2programs, but you can name it whatever you want. 

After adding anything in .bash_aliases you have to restart your terminal to make it work.

---

