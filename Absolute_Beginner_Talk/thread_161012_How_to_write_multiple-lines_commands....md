---
title: "How to write multiple-lines commands..."
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by Amorphous_Snake on 2006-04-16
without pressing enter.

I need quick help please. I am in the middle of installing my video drivers and one command takes more than one line, and I just found out that I don't know how to do it!

---

### Post by halfvolle melk on 2006-04-16
Something like this? (\)

adfgadrfgqerf\
erferfeqfqeerf\
rgedrgg

---

### Post by Amorphous_Snake on 2006-04-16
No like this:

cd /home/user/NVIDIA-Linux-x86-1.0-.....
cc
gcc-3.4
aotahtohaotoaht
athathoatoat

How do you do this?

---

### Post by dermotti on 2006-04-16
i thought you could use && between each command, been awhile tho :-P

---

### Post by halfvolle melk on 2006-04-16
err ...

echo bla && echo diebla && echo diebladiebla

?

---

### Post by Amorphous_Snake on 2006-04-16
I will try it, thanks.

---

### Post by Amorphous_Snake on 2006-04-16
[QUOTE=halfvolle melk]err ...

echo bla && echo diebla && echo diebladiebla

?[/QUOTE]

Should it be like this or ********&&*******&&********** ?

i.e. leave space or not?

Also, if I have a file in home (of my user) and I only have one HD (The default instalation method), then the location of a file will be:

/home/file
/home/user/home/file

or something else completely?

---

### Post by Buffalo Soldier on 2006-04-16
With spaces, example:```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by halfvolle melk on 2006-04-16
[QUOTE=Amorphous_Snake]Also, if I have a file in home (of my user) and I only have one HD (The default instalation method), then the location of a file will be:

/home/file
/home/user/home/file

or something else completely?[/QUOTE]
If it's in the home dir of your user it will be (in my case) at
/home/jz/file

You can use **pwd** to see what dir you're in.

---

### Post by xenmax on 2006-04-16
I always used the semi-colon - ; to seperate commands on same line. Eg:cd x; make; I didn't know abt && - you learn something new everyday :D
Can anyone tell me what is difference between the ';' and '&&'? Thanks.

---

### Post by htinn on 2006-04-16
Commands separated by ; are performed sequentially. Commands separated by && are treated as an expression. So, if you issue:

command1 && command2

Then command2 will only be performed if command1 is successful.

---

### Post by xenmax on 2006-04-16
Thanks htinn. Seems to me like it is better to use && than ;, especially if command2 happens to be a risky one.. i can get away with typos in first command:)

---

