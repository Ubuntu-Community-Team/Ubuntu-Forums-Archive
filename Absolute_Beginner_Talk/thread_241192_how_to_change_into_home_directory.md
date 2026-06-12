---
title: "how to change into home directory"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by k94382 on 2006-08-22
when i open up a terminal i type cd /home and that seems to work fine, but when i try into my folder and desktop it doesnt seem to work. i type cd /home/username/desktop. i cant even change into my folder. any help appreciated

---

### Post by David Corrales on 2006-08-22
The folder Desktop is written with the "D" in capitals. Remember linux is case sensitive :)

---

### Post by k94382 on 2006-08-22
thx, good to know but still doesnt help me. this is wat i try. i cant even change into my directory

klaus@klaus-desktop:~$ cd /home
klaus@klaus-desktop:/home$ cd /klaus
bash: cd: /klaus: No such file or directory
klaus@klaus-desktop:/home$ cd /Klaus
bash: cd: /Klaus: No such file or directory
klaus@klaus-desktop:/home$ cd /Desktop
bash: cd: /Desktop: No such file or directory
klaus@klaus-desktop:/home$

---

### Post by Johan! on 2006-08-22
Type "cd" (without the quotes), and you're in your own home folder (/home/USERNAME)
Then you can type "cd Desktop"

---

### Post by Jagot on 2006-08-22
When you've entered the home directory (cd /home), then type ls to find out the name of the directory of the user(s) and thus whatever your username is.

---

### Post by Johan! on 2006-08-22
~ means you're already in your home folder

---

### Post by GeekSpeek'r on 2006-08-22
ok, so... hold on.

root = /
your home dir = /home/<username>

so

cd /home
 then type     ls

you should see your home directory         yes?

if not reply imediately


therfore, if root = cd /, the nany time you cd /xxxxx you wil be in the folder for the root of the drive (ie: /usr, /bin/ opt, etc......)

so, finally.

cd /home/<your_user_name>
type    ls -l
you should see:
lrwxrwxrwx 1 xxxxx xxxxxx     26 2006-06-21 02:05 Examples -> /usr/share/example-content
drwxr-xr-x 2 xxxxxx xxxxx   4096 2006-08-17 22:00 vmware
drwxr-xr-x 3 xxxxx xxxxxx   4096 2006-08-18 02:11 software
-rw-r--r-- 1 root   root   101715 2006-08-18 02:57 monkey.jpg
drwxr-xr-x 2 xxxxxx xxxxxx  4096 2006-08-19 10:25 Desktop

....or something like that

---

### Post by k94382 on 2006-08-22
oh now i see. i typed cd /desktop (should've done it without the / and also capital) thx everyone

---

### Post by GeekSpeek'r on 2006-08-22
our pleasure

---

