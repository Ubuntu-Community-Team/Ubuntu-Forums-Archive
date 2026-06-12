---
title: "Using CLI, how can I CD into a dir with spaces in the name?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-06-16
Title says it all. Google yielded nothing, search of this forum yielded nothing. So here I am. Simple question.

I got a DIR named misc pics.

Using CLI, how can I CD into it? It just says no file or dir exists.

---

### Post by skymera on 2007-06-16
i dont understand what you mean.

---

### Post by aktiwers on 2007-06-16
```
cd "/misc pics/"
```

---

### Post by Roasted on 2007-06-16
okay...

I'm using command line.
I change directory to home.
I do an LS.
I see Misc Pics is there. Misc Pics is 2 names, with a space in between, for one directory.
How can I change directory (CD) to Misc Pics? 
It tells me no file or directory is found.
I have a strong sense that it's due to the space in this situation.

---

### Post by Roasted on 2007-06-16
> **aktiwers said:**
> ```
cd "/misc pics/"
```

Won't work.

---

### Post by yabbadabbadont on 2007-06-16
As aktiwers already said, you can quote the directory name, just like you would have to do in Windows.  Or you can escape the space (or any other special character).
```
cd "Misc Pics"
cd Misc\ Pics

```
Either should work.

---

### Post by aktiwers on 2007-06-16
Or drag and drop the folder into the Terminal.
But this should work fine:
```
cd "/home/yourusername/Misc Pics/"
```

Remember the Terminal is CaSe SenSiTivE

---

### Post by Roasted on 2007-06-16
Word. When I quoted it, it worked fine. But when I used path to, it didn't.

Thanks dudes.

---

### Post by Anonii on 2007-06-16
> **Roasted said:**
> Word. When I quoted it, it worked fine. But when I used path to, it didn't.

Thanks dudes.
The trick here is either using quotes or using the underated tab-completion. To do the latter, just write the first letters of a dir with spaces, and then use the Tab button to autocomplete it.
For example, if the directory is named "Images and Words", you can type "Imag" and then Tab, that will auto-complete the rest (the examples are obviously without quotes.).

---

### Post by brennydoogles on 2007-06-16
> **Anonii said:**
> The trick here is either using quotes or using the underated tab-completion. To do the latter, just write the first letters of a dir with spaces, and then use the Tab button to autocomplete it.
For example, if the directory is named "Images and Words", you can type "Imag" and then Tab, that will auto-complete the rest (the examples are obviously without quotes.).

Yes, for anyone who uses CLI alot, the tab autocompletion is your friend. If you hit tab and nothing happens, hit it twice and you will see a list of all possible autocompletes, and then you can fill in enough to complaete from there. Wonderful tool.

---

### Post by yabbadabbadont on 2007-06-16
> **brennydoogles said:**
> ... Wonderful tool.

Until you have to use a windows machine.  :lol:

I occasionally find myself hitting tab to try to complete the path of things that I happen to be typing into a forum post...  it is *very* annoying when it doesn't work.  :D

---

### Post by aktiwers on 2007-06-17
> **yabbadabbadont said:**
> Until you have to use a windows machine.  :lol:

I occasionally find myself hitting tab to try to complete the path of things that I happen to be typing into a forum post...  it is *very* annoying when it doesn't work.  :D

Hehe have done the same thing..  or when typing an URL or something :D

---

### Post by arvevans on 2007-06-17
Don't try to make Command Line things harder than they really are:

[INDENT]arv@k7hkl:~$ cd ./.wine
[email]arv@k7hkl:~/.wine[/email]$ ls
dosdevices  drive_c  system.reg  userdef.reg  user.reg
[email]arv@k7hkl:~/.wine[/email]$ cd ./drive_c
[email]arv@k7hkl:~/.wine[/email]/drive_c$ ls
Program Files  windows
[email]arv@k7hkl:~/.wine[/email]/drive_c$ cd ./Prog*
[email]arv@k7hkl:~/.wine[/email]/drive_c/Program Files$ ls
Common Files
[email]arv@k7hkl:~/.wine[/email]/drive_c/Program Files$ [/INDENT]

You can probably see in the "cd Program Files" that I simply resorted to using a wild card (the "*") after the first part of the double word file name.  That usually works.

[INDENT]arv@k7hkl:~/.wine/drive_c$ ls
Program Files  windows
[email]arv@k7hkl:~/.wine[/email]/drive_c$ cd ./'Program Files'
[email]arv@k7hkl:~/.wine[/email]/drive_c/Program Files$ 
[email]arv@k7hkl:~/.wine[/email]/drive_c/Program Files$[/INDENT]

And in that example I put single quotes around the double word file name.  This always works.

For some high sounding words about all of this:
[INDENT]When you are in Command Line mode you are actually using the Shell-Script programming language command interpreter to read and perform your commands.  Thus, the "Regular Expression Matcher" (called "regx") is actually working within the bash (shell programming language) to interpret what you entered as a program command.  To get a better idea of how this works you could, at the command line prompt, enter "man bash" and then use your arrow keys to scroll down/up in the manual page for this very powerful command interpreter.  [/INDENT]

After reading over the man page on bash, you may suddenly realize that you can string shell or bash commands together to form short fast programs.  Welcome to the Linux Command Line programming world.  :D

_._

---

