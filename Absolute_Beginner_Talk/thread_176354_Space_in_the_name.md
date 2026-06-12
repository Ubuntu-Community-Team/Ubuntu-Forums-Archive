---
title: "Space in the name"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Compact on 2006-05-14
How can I open a folder by terminal with a space in the file/folder name? I mean cd xxx[space]xxx.

---

### Post by Rinzwind on 2006-05-14
cd a\ b/

(you need to escape the space)

edit:
rinzwind@diskworld:~$ mkdir "a b"
rinzwind@diskworld:~$ ls
a b      
rinzwind@diskworld:~$ cd a\ b/
rinzwind@diskworld:~/a b$ pwd
/home/rinzwind/a b
rinzwind@diskworld:~/a b$


EASIEST would be 
cd a
and then TAB ;)

---

### Post by aysiu on 2006-05-14
```
cd "xxx xxx"
```

---

### Post by DSn0wMan on 2006-05-14
[QUOTE=Compact]How can I open a folder by terminal with a space in the file/folder name? I mean cd xxx[space]xxx.[/QUOTE]

As far as I know the terminal doen't recognise spaces in a file name. It thinks your entering additional commands.

Try finding the file with file brownse (gui) and taking the spaces out of the name. Some times underscores are usefull "_"

---

### Post by DSn0wMan on 2006-05-14
[QUOTE=DSn0wMan]As far as I know the terminal doen't recognise spaces in a file name. It thinks your entering additional commands.

Try finding the file with file brownse (gui) and taking the spaces out of the name. Some times underscores are usefull "_"[/QUOTE]

I stand corrected. Still it's a good idea not to use spaces if you can avoid it.

---

### Post by Rinzwind on 2006-05-14
[QUOTE=aysiu]```
cd "xxx xxx"
```[/QUOTE]


I changed my reply ;)

1st post was wrong. Edit is correct (tried and proven)

:+

---

### Post by Kvark on 2006-05-14
[QUOTE=DSn0wMan]I stand corrected. Still it's a good idea not to use spaces if you can avoid it.[/QUOTE]
Space is one of the most used characters in English and many other languages. I'm pretty sure it is one of the 5 most used. There is nothing wrong at all with using it in names.

If the dir is named "image album" or "image_album" then type "ima" and hit tab. It'll fill in the full name in either case so it is just as easy regardless of if you use a normal space or some weird replacement character. Or use any of the other solutions mentioned here.

---

### Post by DSn0wMan on 2006-05-14
I guess I am just a little weird. I think I picked up the habbit of no spaces in file names back when I was learning C++. Who knows thats probably changed now to.

Although they do come in handy for lots of other things. :D

Thats a good point about the tab completion.

---

### Post by Rinzwind on 2006-05-14
The fun starts when you  do
mkdir " test"

No tab-completion hmmm ;)

Then you must do:
cd \ test

So it's better to remember you can ALWAYS escape a space.

---

### Post by ComplexNumber on 2006-05-14
>  No tab-completion hmmm
bash-completion is a package i couldn't do without for terminal usage, and i would recommend it to everyone.

---

### Post by Kvark on 2006-05-14
[QUOTE=ComplexNumber]bash-completion is a package i couldn't do without for terminal usage, and i would recommend it to everyone.[/QUOTE]
```
$aptitude show bash-completion
Package: bash-completion
Status: not a real package
```
:?

---

### Post by ComplexNumber on 2006-05-14
[quote=Kvark]```
$aptitude show bash-completion
Package: bash-completion
Status: not a real package
``` :?[/quote] its odd that it shows that. other people using ubuntu seem to have downloaded it ok. i use FC5, so i got it from [here]("http://rpm.pbone.net/index.php3/stat/4/idpl/2690565/com/bash-completion-20060301-1.fc5.noarch.rpm.html")__.

---

