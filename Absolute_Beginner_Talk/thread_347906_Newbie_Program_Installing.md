---
title: "Newbie Program Installing"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by JBen on 2007-01-28
Hello, I'm running Dapper Drake and I cannot figure out how to install a program. I have a .run file and when I type ./filename.run into the terminal it says "No such file or directory." I do not know how to install this file.

---

### Post by taurus on 2007-01-28
Maybe you saved that file to ~/Desktop so you need to change into that directory first.

```
cd ~/Desktop
chmod 755 **filename**
./**filename**
-or-
sudo ./**filename**
```

p.s.  What are you trying to install anyway?

---

### Post by JBen on 2007-01-28
I tried both of those commands, The first one says "cannot access 'filename': No such file or directory. The second one asks me for my password, which I type in and then it says sudo: ./filename:command not found

---

### Post by JBen on 2007-01-28
Long story short: I'm trying to install two different games to determine if my video card will support 3d games. Savage1 and Legends are the games I'm trying to install.

---

### Post by MkfIbK7a on 2007-01-28
did you replace the **filename** in those instructions with the name of your  .run file?

if not do it

wert

---

### Post by JBen on 2007-01-28
> **wert613 said:**
> did you replace the **filename** in those instructions with the name of your  .run file?

if not do it

wert

Yes I replaced filename with ./legends_linux-0.4.1.42.run

---

### Post by taurus on 2007-01-28
What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by JBen on 2007-01-28
total 142476
drwxr-xr-x  8 jordan jordan      4096 2007-01-27 22:48 .
drwxr-xr-x 30 jordan jordan      4096 2007-01-27 22:55 ..
drwxr-xr-x  2 jordan root        4096 2007-01-04 15:22 install_flash_player_9_linux
-rw-r--r--  1 jordan root     2609703 2007-01-18 20:34 install_flash_player_9_linux.tar.gz
drwxr-xr-x  2 jordan jordan      4096 2007-01-27 22:48 Legends
-rw-r--r--  1 jordan jordan 121687045 2007-01-06 18:56 legends_linux_0.4.1.40.shdrwxr-xr-x 33 jordan jordan      4096 2007-01-03 21:02 MPlayer-1.0rc1
-rw-r--r--  1 jordan jordan   8414213 2007-01-03 20:35 MPlayer-1.0rc1.tar.bz2
-rw-r--r--  1 jordan root     2184139 2007-01-27 19:56 p7zip_4.44_x86_linux_bin.tar.bz2
drwxr-xr-x  3 jordan root        4096 2007-01-27 19:30 Savage
-rw-r--r--  1 jordan jordan    152412 2007-01-03 17:49 tahoma.ttf.tar.gz
drwxr-xr-x 11 jordan jordan      4096 2007-01-27 21:13 thunderbird
-rw-r--r--  1 jordan jordan  10629213 2007-01-03 17:39 thunderbird-1.5.0.9.tar.gz
drwxr-xr-x  3 jordan root        4096 2007-01-27 20:37 untitled folder

---

### Post by MkfIbK7a on 2007-01-28
i dont see that file...

there are a few legends mentioned but no .run

---

### Post by JBen on 2007-01-28
Woops, that .run file was in the Legends folder. I have moved it out of that folder on the the Desktop. I typed in ./legends_linux-0.4.1.42.run and it said Permission denied.

---

### Post by MkfIbK7a on 2007-01-28
do 
sudo ./legends_linux-0.4.1.42.run

---

### Post by JBen on 2007-01-28
> **wert613 said:**
> do 
sudo ./legends_linux-0.4.1.42.run


sudo: ./legends_linux-0.4.1.42.run: command not found

---

### Post by taurus on 2007-01-28
```
chmod 755 legends_linux_0.4.1.40.sh
./legends_linux_0.4.1.40.sh
```

---

### Post by MkfIbK7a on 2007-01-28
yes it was probably better to change the mode...

---

### Post by JBen on 2007-01-28
YAY! that worked, however, that version of legends is the version prior to the latest.

---

### Post by MkfIbK7a on 2007-01-28
you should search google for the newest version

here i found a bebian installer click the download link, post everything that heppens here and i will help

[http://legendsthegame.net/index.php?m=fileswap&view=80](http://legendsthegame.net/index.php?m=fileswap&view=80)

**_EDIT_**: sorry i hope this is the program you wanted...

---

### Post by JBen on 2007-01-28
I have that file downloaded and I have the same file but it is a .run file. I used the same steps  to install this file and it says that legends was updated sucessfully. I did cd /home/jordan/legends then did ./legends but the game will not run now.

---

### Post by taurus on 2007-01-28
```
ls -la /home/jordan/legends
```

---

### Post by JBen on 2007-01-28
I'm a moron, the command was ./RUNlegends, not just ./legends! Thank you both for your help! Could you suggest a guide to learning these commands? Prior to this thread, I did not know that you had to cd to switch to a directory to run a file.

---

### Post by MkfIbK7a on 2007-01-28
paste the output of

legends

if that does nothing do

cd /home/jordan/legends/
ls

then paste the output

---

### Post by taurus on 2007-01-28
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by MkfIbK7a on 2007-01-28
woah ok that was fast

anyhow cd is just like in dos

you can probably google 
"bash commands"
and find something

sorry i dont know any specific guides

---

### Post by JBen on 2007-01-28
Yay! the game works and so this means that the other game doesn't work because it doesn't like me. Thank you for your help!

---

