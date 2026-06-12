---
title: "Aliases Problem"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by tane_stelzer on 2005-10-23
I want to make an alias like this alias beep\ media\ player=`LC_ALL=zh_CN.gb2312 beep\ media\ player`
well i am not to sure if this is right, well i just want to open the BMP with chinese support kind of thing. An this is the only way i can start the BMP with it. Please help me thanks
tane

---

### Post by darth_vector on 2005-10-24
hi,

as far as i know you cant, but there is a workaround. follow the steps below:

1) if you dont already have a /bin directory in your home directory, make one
>cd $HOME
>mkdir bin

2) add it to your path by adding the following line to the file .bashrc in your home directory

PATH=$PATH:~/bin

3) go to your bin directory and make a file with the name you want for the command. then make this file executable

eg.
>cd $HOME/bin
>touch player
>chmod u+x player

4)open the file (now a script) in your favourite text editor and write the name of the command you want executed 

eg.
/usr/bin/player --gui --chinese

5)in future, whenever you want to use the player you just type the name of the script

hope that helps

---

### Post by tane_stelzer on 2005-10-24
Well i already have a script on my desktop which opens the BMP with the chinese support. What i tried to do was to open the BMP with chinese support all the time so every link opens with the chinese support. I tried the alias cos the command in the link was "beep-media players". I tried the alias to change that coommand. But it didn't work. My question now is how can i open any link of BMP with the chinese support.

---

