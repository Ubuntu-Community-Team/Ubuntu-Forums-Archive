---
title: "bash or shell command"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by bellzii on 2007-06-28
hey i want to know how can i open a txt file using the terminal,  i tried doing it executable, but i think im just screwing up

---

### Post by EndPerform on 2007-06-28
Nano is a good editor to try:

```
nano file.txt
```

That will open the file for you.  To get out of nano, CTRL-X to exit.


If it's a small file, you can dump the output to your terminal with this:
```
cat file.txt
```

Obviously, replace file.txt with the filename you want to open :)

---

### Post by hyper_ch on 2007-06-28
hmm, you use a command line editor :)

```

nano file.txt

```

Exit the file:
```

ctrl+x

```

or you could use some other command line editor like "vi"

---

### Post by bellzii on 2007-06-28
i know i can use editor "filename"  but i need it to open in an external text editor window

---

### Post by speaker219 on 2007-06-28
> **bellzii said:**
> need it to open in an external text editor window

use:
```
sudo gedit file.txt
```
(replace file.txt with the file you want to open)

---

### Post by bellzii on 2007-06-28
how can i save the file after i finish, if i edited it in the terminal

thanks alot

---

### Post by Ayuthia on 2007-06-28
Are you saying that you want to use an editor like gedit?  The command would be something like:

gedit something.txt

Bascially, the command at the terminal would be <application> <file>.

Oops.  Not fast enough...

---

### Post by meatpan on 2007-06-28
It sounds like you want to launch a graphical editor from the command line.  If so, you have quite a few options.

1. Default ubuntu desktop, run 'gedit'
2.  If you are using kubuntu, run 'kedit'
3. You can run 'ooffice' and start an open office text document
4. If installed, try running 'abiword'.  i'm not sure if this is in the default install.  Probably not.

EDIT:  Looks like everyone replied at once, so this post is redundant.  Please see above posts.

---

### Post by bellzii on 2007-06-28
what if i wanna save the file i edited while its open in the terminal

---

### Post by speaker219 on 2007-06-28
> **bellzii said:**
> what if i wanna save the file i edited while its open in the terminal
if you want to save a file after editing it in terminal with nano, press Ctrl+O.
There is more information on nano here:
[http://www.gentoo.org/doc/en/nano-basics-guide.xml](http://www.gentoo.org/doc/en/nano-basics-guide.xml)

---

### Post by hyper_ch on 2007-06-28
You can press  CTRL-X in nano... this will close the file... but if it was altered you will then be asked if you want to save or abort or not save... and then you can enter the filename (if it shall be saved as)

---

