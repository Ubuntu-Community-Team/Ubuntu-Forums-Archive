---
title: "File Names"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by sKuarecircle on 2006-10-10
Quick one, with regard to file names, and i am referring to everything here, joegs, spreadsheets, word(open Office) documents basically anythiing I name or rename, is it best practise to replace the spaces in filenames with underscores or is it fine to just leave spaces. I would like to know now if it's a issue rather than 4 weeks down the line find out either I have been wasting my time using underscores or on the flipside of the coin, I should habe been and haven't.

Shot guys

---

### Post by mssever on 2006-10-10
Strictly speaking, you can use absolutely any printable chracter in filenames except for the slash (/). However, if you're working from the command line, you have to remember to escape spaces and other funny characters. If you're working in a graphical environment (e.g., Nautilus, OpenOffice), you don't have to worry about escaping anything.

I regularly use spaces, question marks (?), etc. without difficulty.

---

### Post by oyvindaa on 2006-10-10
Personally, I think it's best to keep the underscores.

If you were to perform file operations from within the terminal, it'd be slightly more difficult with spaces in file names.

cp /home/user/this\ file /usr/share/pixmaps (spaces)

cp /home/user/this_file /usr/share/pixmaps (underscore)

There might be other pros and cons, I'm not sure.

---

### Post by bodhi.zazen on 2006-10-10
It makes no real difference.

When working with the command line you will need to "escape" the white space.

If your file name is "file name" this becomes "file\ name".

There is an easier way, use tab completion. This will get the syntax correct:

file<tab> will expand to become file\ name

---

### Post by sKuarecircle on 2006-10-10
Thanks for th ersponse guys, personally I think I may just stick to underscores for now, I realise for a more experienced user it makes no difference, but the more i can simplify my life now the better

---

### Post by anaconda on 2006-10-10
There still are some programs, which can't handle spaces in filenmes. So I use underscores eg. "file_name" or big letters like in: "FileName"

---

