---
title: "Help finding files in the command line"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by climatewarrior on 2007-12-17
Is there a way I can use find in the command line when I dont know the exact file name

For example right now if I want to look for something what I do is find -name "filename"
but what if I dont know the exact name of the file, how can I look for it using find or another command?

Thanks Guys

---

### Post by diatribe on 2007-12-17
use locate and a protion of the file name and it will find it

---

### Post by jba6511 on 2007-12-17
if you know part of the file name or the extension you can use the * character.

for example

sudo find / -name *.txt 

this would find all txt files

---

### Post by climatewarrior on 2007-12-17
Thanks! That is precisely what I needed. Nothing beats community support.

---

### Post by amac27 on 2007-12-17
usually what I do since I know the file that I'm looking for I'll open a terminal and type this

whereis [filename]

I do this when i'm on the root. It will display the location of the file if there is a match so you can just 

cd [then the directory]

hope that helps

---

