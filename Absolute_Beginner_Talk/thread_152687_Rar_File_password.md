---
title: "Rar File password"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by dead_man_walking on 2006-03-30
Well i was opening a rar file which was password protected by me....so when i opened it with archive manager ......it gave a error that password was wrong ....when infact i did not get a chance to enter the password .....what should i do????

---

### Post by meborc on 2006-03-30
where did you rar'd this file? in windows or in linux? ... how did you set the password?

---

### Post by dead_man_walking on 2006-03-30
Well.....i put the password in windows and then after installing ubuntu i tried to copy them from the cd i had .....but without asking for password it tells me that i supplied an incorrect password

---

### Post by meborc on 2006-03-30
hehe... :) i really don't think that it works this way... the program you used to rar the file was? winrar? and in ubuntu u used archive manager?

different programs, different coding systems...

---

### Post by dead_man_walking on 2006-03-31
but thats the only option i have ... i have installed rar fromsynaptic but the rar stuff always opens with archive manager ...and then i extract stuff and archive manager worked well with the other folders except for this one!!!....is there any other solution

---

### Post by jeremy on 2006-03-31
Have you tried using the console?

---

### Post by dead_man_walking on 2006-03-31
Well!!! ..... i am totally new to linux so i dont know what to do ...what to type in the terminal

---

### Post by firehead on 2006-03-31
try ```
unrar e file-to-unrar
``` this will extract the files in the current directory and you will be prompted for a password (and don't panick if you see no asterisks or anything while typing your pass,that' deliberate).if it says something like ```
-bash: unrar: command not found
``` you have to install unrar first. connect to the inet and type :```
sudo apt-get update
sudo apt-get install unrar
``` or use any other package manager...

---

### Post by dead_man_walking on 2006-03-31
But i have already installed unrar using synaptic ... and i can extract rar files using archive manager....it never gives me an option to open files with unrar so i have to use archive manager  but archive manager never asks for password for the file and straight away goes on to extract from the file.....and then returns an error of incorrect password

---

### Post by megamania on 2006-03-31
[QUOTE=dead_man_walking]Well i was opening a rar file which was password protected by me....so when i opened it with archive manager ......it gave a error that password was wrong ....when infact i did not get a chance to enter the password .....what should i do????[/QUOTE]

did you "drag and drop" the files?

Instead, try selecting the files first, and then choose "extract". you should be able to enter the password there.

---

### Post by dead_man_walking on 2006-03-31
it worked:mrgreen: :p  thanx bro

---

### Post by megamania on 2006-03-31
[QUOTE=dead_man_walking]it worked:mrgreen: :p  thanx bro[/QUOTE]

Glad to hear that I could help!

---

### Post by typebox7000 on 2006-06-25
[QUOTE=megamania]did you "drag and drop" the files?

Instead, try selecting the files first, and then choose "extract". you should be able to enter the password there.[/QUOTE]


I have had the same problem attempting to extract some .rar files that are password protected. If I merely click on them I get an incorrect password prompt. If I select and choose "extract here", it just creates a new file folder.
It does this in both "Archive Manager" and "File Roller". Neither gives me the option of entering the password.

Any suggestions?

---

### Post by St0neD_JunioR on 2006-07-02
[QUOTE=typebox7000]I have had the same problem attempting to extract some .rar files that are password protected. If I merely click on them I get an incorrect password prompt. If I select and choose "extract here", it just creates a new file folder.
It does this in both "Archive Manager" and "File Roller". Neither gives me the option of entering the password.

Any suggestions?[/QUOTE]

SAME problem here :neutral:

---

