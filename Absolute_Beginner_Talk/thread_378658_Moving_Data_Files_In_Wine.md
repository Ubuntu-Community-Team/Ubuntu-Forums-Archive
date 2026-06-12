---
title: "Moving Data Files In Wine"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by jretzer on 2007-03-07
I got my classroom crossword puzzle program working in wine. Now I'm wondering how to move the file from the c drive to a memory stick so I can take the file to another computer and print it.

I've looked at winefile, but drag and drop doesn't seem to work.

TIA

---

### Post by eljalill on 2007-03-07
I am far from being an expert myself, which is why I might ask a very stupid question back here.... But why don't you just use a terminal and cp (copy) or mv (move) ? Besides the context menu also works fine for me.... :)

---

### Post by jretzer on 2007-03-08
> **eljalill said:**
> I am far from being an expert myself, which is why I might ask a very stupid question back here.... But why don't you just use a terminal and cp (copy) or mv (move) ? Besides the context menu also works fine for me.... :)

I'm missing fundamental here, because copy and move don't seem to do anything.

---

### Post by anaconda on 2007-03-08
then you can just use the normal "File browser" (=nautilus) 
just select the View>Show Hidden Files   
option first.

I dont know whre you have the .wine -folder, but mine is at my home directory.
so I would just have to go to 
~/.wine/drive_c
and I would be in wines C drive.. 
then just drag&drop the file to where you want it..

PS. cp command works like this:
cp from_where to_destination

---

