---
title: "export PATH=$PATH: etc...help"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by nite owl on 2006-11-19
Hi, when I create my shell scripts I’d like to run them by just stating their name; for example when I save a script all I have to do is type their name in my terminal and it will execute (i.e. `my_script`) and nothing else. I realise to do this to my understanding is to put the statement export PATH=$PATH:/home/bin/…Which is the directory my scripts are saved in. However I’ve found that I have to put this in my .bashrc file for it to work in the program Terminal on my GUI. But for it to work in the other non-gui terminal (CTRL+ALT+F1 etc...) I have to add that statement to my .bash_profile as well. If I don’t add it to both they will only work with one as I stated. As I am new to Linux I do not know the specifics and I am just putting this statement in any arbitrary space in these files, basically just anywhere. Is there a spot I should place this statement in one of my files that it will work across the board without me having to put it in both these files for it to work. Thanks for any advice anyone could give me.

---

### Post by bodhi.zazen on 2006-11-19
> **nite owl said:**
> Hi, when I create my shell scripts I’d like to run them by just stating their name; for example when I save a script all I have to do is type their name in my terminal and it will execute (i.e. `my_script`) and nothing else. I realise to do this to my understanding is to put the statement export PATH=$PATH:/home/bin/…Which is the directory my scripts are saved in. However I’ve found that I have to put this in my .bashrc file for it to work in the program Terminal on my GUI. But for it to work in the other non-gui terminal (CTRL+ALT+F1 etc...) I have to add that statement to my .bash_profile as well. If I don’t add it to both they will only work with one as I stated. As I am new to Linux I do not know the specifics and I am just putting this statement in any arbitrary space in these files, basically just anywhere. Is there a spot I should place this statement in one of my files that it will work across the board without me having to put it in both these files for it to work. Thanks for any advice anyone could give me.

You can use a single file.

Backup ~/.bash_profile

Replace the contents (of bash_profile) with:

> # Use a single file: .bashrc

source ~/.bashrc

---

