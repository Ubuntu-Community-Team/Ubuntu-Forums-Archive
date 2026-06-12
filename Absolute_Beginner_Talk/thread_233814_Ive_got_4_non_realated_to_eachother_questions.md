---
title: "Ive got 4 non realated to eachother questions"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-08-10
1. How do you run an sh file?

2. Cant the Terminal open files with spaces?

3. How do search for hidden files? Like my wine folder is called .wine but when I try and serach for it under Places>Search for file, it cant find it.

4. Does anyone have a guide for the program gdesklets? Its suppose to make me an osx like panel, but I have no idea how to use it.

---

### Post by meng on 2006-08-10
1. Suppose the file is what.sh, and you're in the directory
chmod +x what.sh (if not already executable)
./what.sh

2. Use "\ " to indicate space. Suppose the file is "what the.doc", then use syntax like
cat what\ the.doc
(Read up about escape characters.)

3. ls -a

4. It's fairly intuitive, but you could probably google it if you need to.

---

### Post by jincast90 on 2006-08-10
> **meng said:**
> 
3. ls -a


Isint ls -a only in the terminal?

Otherwise thanks for the other answers, I figured question 1 and 2 out with the help from you, and ill see what I can find googling gdesklets

---

### Post by msak007 on 2006-08-10
Your questions have (mostly) been answered, but just thought I'd add something

1. You can also use "sh <name of file>"

2. Some people find it easier to enclose the name of the path or file with spaces in it in quotes rather than using escape characters (gets annoying if you have a long path with lots of spaces), so in the example above the you would issue the command cat "what the.doc"


3. "ls -a" is a terminal command, but it's only useful for listing hidden files in the current directory you're in - doesn't help in the situation posed above if you're looking for the file / folder and don't know where it's at. I don't use graphical search at all, but I do search using the terminal with the "find" command.

---

### Post by meng on 2006-08-10
There's an option in the Nautilus folder somewhere for viewing hidden files/directories. Also if you're in terminal and start typing "cat what" then press TAB you'll get an autocompletion.

---

### Post by jincast90 on 2006-08-10
Ok so I found out how to run sh files, but when doing so, it tells me this

In Terminal:

Platform:   X86
System:     LINUX
avis input: no
mp4 output: no
pthread:    no
vfw:        no
debug:      no
visualize:  no

You can run 'make' now.

What does You can run make now. Mean?

---

### Post by kurup on 2006-08-10
> **jincast90 said:**
> 3. How do search for hidden files? Like my wine folder is called .wine but when I try and serach for it under Places>Search for file, it cant find it.
Alt+F2 -> Type "nautilus" 
Ctrl+H should show you the 'hidden' files

> **jincast90 said:**
> 4. Does anyone have a guide for the program gdesklets? Its suppose to make me an osx like panel, but I have no idea how to use it.
Follow this thread..its fairly simple.
[http://ubuntuforums.org/showthread.php?t=200892](http://ubuntuforums.org/showthread.php?t=200892)

---

### Post by msak007 on 2006-08-10
Well it depends on what the script was supposed to do. What script are you trying to run / where did you download it from? Some scripts install an app for you, some simply configure everything for you in order to prepare the app for installation. Normally when compiling programs from source that are not in the repositories, you do the following after downloading the files:

```
./configure
make
make install
```

It sounds like the script did the "./configure" part for you, so now simply type

```
make
```

Once that's completed without errors, type
```
sudo make install
```

---

