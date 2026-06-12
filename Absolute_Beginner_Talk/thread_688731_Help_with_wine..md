---
title: "Help with wine."
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by darkenigma02 on 2008-02-05
How do you make a .bat file run with Wine?


Code(It's in the .bat)- 
```

@title Sinscape Client

@java -cp ./SinScape.jar -Xmx500m client

@pause


```

---

### Post by bump_ on 2008-02-05
CD to the directory where the .bat is stored and type

```
wine cmd.exe
```

It will start a command prompt from that directory like in Windows. Then just run the .bat file like you normally would.

---

### Post by darkenigma02 on 2008-02-05
I cant CD up to it, it says that the folder containing the .bat isnt a command, and when i try to cd all the way through home, it says its not a file or a directory

---

### Post by darkenigma02 on 2008-02-05
Ok, I CD'd upto it, but I dont know how to open the run.bat now.

---

### Post by bump_ on 2008-02-05
Ok if you are in the directory with example.bat, type

```
wine cmd.exe
example.bat
```

And it should run example.bat in the terminal as it would in a Windows command prompt.

---

### Post by darkenigma02 on 2008-02-05
Uhh...

I wasnt able to CD upto it without typing wine cmd.exe FIRST, and then when I did run.bat, nothing happened..

OK, I got to the folder, did wine cmd.exe, and i typed run.bat, and it said it wasnt there, then I did run.bat~ (was in the ls list) and it said access denied

---

### Post by bump_ on 2008-02-05
Whether you changed the directory first or started cmd.exe first, the result should be the same. Here is an example:

Say I have test.bat on my Desktop. I could either change directory first then run cmd::

```
bump@bump-laptop:~$ cd Desktop/
bump@bump-laptop:~/Desktop$ wine cmd.exe

CMD Version 0.9.54

Z:\Desktop>test.bat
"hello"
Z:\Desktop>

```

or I could start cmd first, then change directory:

```
bump@bump-laptop:~$ wine cmd.exe

CMD Version 0.9.54

Z:\>cd Desktop
Z:\Desktop>test.bat
"hello"
Z:\Desktop>

```

That is the simplest way I know to do it. Maybe someone else knows a simpler.

---

### Post by darkenigma02 on 2008-02-05
OK, I got to the folder, did wine cmd.exe, and i typed run.bat, and it said it wasnt there, then I did run.bat~ (was in the ls list) and it said access denied

---

### Post by bump_ on 2008-02-05
Files that end with ~ are backup files.

Which folder is this .bat file in? Even if I put mine in / it runs with no problems. Post a transcript of the commands and errors you use and get.

---

### Post by darkenigma02 on 2008-02-05
```
kyle@kyle-desktop:~$ cd /home/kyle/Desktop/Sinscape
kyle@kyle-desktop:~/Desktop/Sinscape$ wine cmd.exe
CMD Version 0.9.54

Z:\home\kyle\Desktop\Sinscape>Run.bat
File not found

Press Return key to continue: kyle@kyle-desktop:~/Desktop/Sinscape$ 
kyle@kyle-desktop:~/Desktop/Sinscape$ run.bat
bash: run.bat: command not found
kyle@kyle-desktop:~/Desktop/Sinscape$ 
kyle@kyle-desktop:~/Desktop/Sinscape$ run.bat
bash: run.bat: command not found
kyle@kyle-desktop:~/Desktop/Sinscape$ wine cmd.exe
CMD Version 0.9.54

Z:\home\kyle\Desktop\Sinscape>run.bat
File not found

Press Return key to continue: 


```


run.bat is in there though, I just checked

---

### Post by bump_ on 2008-02-05
Are you sure run.bat is in this folder on your desktop? Because as far as I can tell, it doesn't look like it. What does 

```
ls ~/Desktop/Sinscape
```

give as output?

---

### Post by darkenigma02 on 2008-02-05
the run.bat is in there. I just checked.
```
kyle@kyle-desktop:~/Desktop/Sinscape$ ls ~/Desktop/Sinscape
cache   Read This To Play.txt  run.bat~      sinscape.jpg
Models  run.bat                Sinscape.jar  Sprites
kyle@kyle-desktop:~/Desktop/Sinscape$ 

```

edit-

I tried opening some of those, and all I got was access denied.

---

### Post by bump_ on 2008-02-05
I am at a loss. You should have full read write privileges to your dekstop. Post the output of 

```
ls -l ~/Desktop/Sinscape
```

---

### Post by darkenigma02 on 2008-02-05
kyle@kyle-desktop:~/Desktop/Sinscape$ ls -l ~/Desktop/Sinscape
total 768
drwxr-xr-x 3 kyle kyle   4096 2008-02-01 21:32 cache
drwxr-xr-x 2 kyle kyle   4096 2008-02-01 20:16 Models
-rw-r--r-- 1 kyle kyle    501 2008-02-01 21:41 Read This To Play.txt
-rw-r--r-- 1 kyle kyle     75 2008-02-01 21:22 run.bat
-rw-r--r-- 1 kyle kyle     72 2008-01-08 00:34 run.bat~
-rw-r--r-- 1 kyle kyle 327980 2008-02-01 20:16 Sinscape.jar
-rw-r--r-- 1 kyle kyle 420292 2008-01-04 18:50 sinscape.jpg
drwxr-xr-x 2 kyle kyle   4096 2008-02-01 20:16 Sprites
kyle@kyle-desktop:~/Desktop/Sinscape$

---

### Post by darkenigma02 on 2008-02-05
any help?

---

### Post by darkenigma02 on 2008-02-05
Anybody? please?

---

### Post by darkenigma02 on 2008-02-05
..

---

### Post by doorknob60 on 2008-02-05
See my post [http://ubuntuforums.org/showpost.php?p=4277492&postcount=11](http://ubuntuforums.org/showpost.php?p=4277492&postcount=11) there if you haven't already. Also your name sounds familiar...do you play runescape or something?

---

### Post by jayman21 on 2008-03-05
try changing the permissions on your bat file to execute - 770

---

