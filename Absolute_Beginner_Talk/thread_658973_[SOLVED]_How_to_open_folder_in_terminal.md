---
title: "[SOLVED] How to open folder in terminal"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by My_Ausweis on 2008-01-05
Dear All

How to open folder in terminal using command cd

for example my folder is : saya lagi

how to open folder saya lagi using cd command 

thx

---

### Post by ubutufan on 2008-01-05
Assuming that the folder is placed in home directory you type

cd /home/the_name_of_the_folder_you_want_opened

---

### Post by happyhamster on 2008-01-05
- You can work around the space in the folder name by using quotes:

cd "saya lagi"

- Or you can "escape" any special character by putting a \ before it:

cd saya\ lagi

- Or just make use of the autocomplete feature using the tab key:

Type:     cd sa     and then just press the tab key so that linux can automatically complete the line for you. This only works if there are no other folders that begin with the letters "sa", else you should try  "cd say" and tab or "cd saya" and tab, etc. If you press tab twice you'll get a list of possible folder names.

Lastly, in case you use regular ubuntu (Gnome/nautilus) you can install the package nautilus-open-terminal, that will allow you to right-click a folder and start a terminal from there.

---

### Post by Bruce M. on 2008-01-05
> **My_Ausweis said:**
> Dear All

How to open folder in terminal using command cd

for example my folder is : saya lagi

how to open folder saya lagi using cd command 

thx

I created "saya lagi" on my system and when I CD'd to it, it didn't work either.
```

bruloo@The-Team:~$ cd saya lagi
bash: cd: saya: No such file or directory
bruloo@The-Team:~$ 

```

I also have:

```

bruloo@The-Team:~$ cd Inkscape Tutorials
bash: cd: Inkscape: No such file or directory
bruloo@The-Team:~$ 

```

It doesn't get to the second name
So I renamed them with an underscore for the space. ie: saya_lagi

```

bruloo@The-Team:~$ cd saya_lagi
bruloo@The-Team:~/saya_lagi$ cd
bruloo@The-Team:~$ cd Inkscape_Tutorials
bruloo@The-Team:~/Inkscape_Tutorials$ cd
bruloo@The-Team:~$ 

```

That worked perfectly

Check out: [Linux bash commands - MAN pages]("http://www.ss64.com/bash/"), there is no reference to folders with "two" names.  :(

Doesn't answer your question *completely* but it's a working start.

Bruce

---

### Post by hyper_ch on 2008-01-05
as already pointed out:

```

cd "saya lagi"

```
or
```

cd saya\ lagi

```

---

### Post by Alx c on 2008-01-05
It opens in the same way as in windows terminal:cd and what ever the directory is.

---

