---
title: "2 questions, mouse pointer and commands"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Spacedementia87 on 2007-09-03
Right, my first problem is that i can't see my mouse pointer so i am just constantly pressing CTRL to find out where I am.

Running 7.04 and have a Nvidia 6600 GT GFX card.

Some one told me it was to do with the hardware mouse pointer and to disable it.  I don't know how though.

The second is a question on how do you actually create a new file.

So say i wanted to make a new text file on a drive from the terminal.  Probably very easy but would just like to know before i do something stupid!

---

### Post by kebes on 2007-09-03
> **Spacedementia87 said:**
> The second is a question on how do you actually create a new file.

So say i wanted to make a new text file on a drive from the terminal.  Probably very easy but would just like to know before i do something stupid!

I don't know about your mouse pointer issue. But this is very easy. To create a new file called "newfile" just do:
```

touch newfile

```

"touch" is a command that updates the timestamp on any file--if the file doesn't exist then it creates a new empty file with that name. Very handy way to create an empty text file.

Of course you can also just edit a new file, like:
```

nano newfile

```
And then just save the file on exit.

---

### Post by Spacedementia87 on 2007-09-03
yeah, thought it would be something like that.

Thank you :)

Anyone know about the mouse pointer?

---

### Post by Billy_McBong on 2007-09-03
[COLOR="Blue"]not sure about the mouse but to make a new text file from the terminal you would just do
```
gedit name_of_file
```
EDIT:you all type to fast :D[/COLOR]

---

### Post by Paul133 on 2007-09-03
You want to write a new file from the terminal? ```
nano FILENAME
``` will make a new text file with FILENAME, and let you write in it. When you're done, Ctrl-O will save it (press enter to confirm the name) and Ctrl-X will exit nano and bring you back to the commandline.

A little background: touch lets you create a new empty file. nano is a commandline text editor. gedit will open a new window with a graphical text editor. That might not work so well if you don't have a mouse.

---

