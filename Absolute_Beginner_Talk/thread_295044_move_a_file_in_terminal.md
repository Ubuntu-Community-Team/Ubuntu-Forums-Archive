---
title: "move a file in terminal"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by marmiteOlz on 2006-11-07
k i am a noob
i  am trying to move the file for flashplayer add on for firefox
its the .so extension
i read it has to be placed in the /usr/lib/firefox/plugins  folder
but how in terminal?
it wont let me copy n paste through drag and drop method ( im a noob so i dunno why)
what would be the code in a terminal window?
folder i downlaoded it is called flash-player-plugin-9.0.21.55
file is called libflashplayer.so

and any idea where i can find a list of commands a noob would understand?

---

### Post by GStubbs43 on 2006-11-07
I believe it would be ```
sudo [mv]("http://unixhelp.ed.ac.uk/CGI/man-cgi?mv") /path/to/file /new/path/ 
```

---

### Post by BatteryCell on 2006-11-07
This always is a good referece:
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

And as to basic commands Ill just make a list that if anyone thinks needs to be added on to just post. Ok so:
```
ls
```
This lists contents of a directory.  Some common uses of ls are "ls -l" to see detailed info and "ls -a" to see all files (including hidden ones)
```
cd
```
This changes the directory, allowing you to move around your computer in the terminal.  "cd /path/to/somedir" will take you to the directory represented by /path/to/somedir.  "cd .." brings you up one level in the directory structure.
```
cp
```
This copies one file to another.  
"cp /path/to/file/to/be/copied /path/to/where/you/want/it/copied"
```
mv
```
This moves a file, also can be used to rename the file. mv uses the same syntax as cp.
```
rm
```
This removes a file, be careful though because the deletion cant be undone. 
"rm /path/to/file" removes file in the /path/to directory.
Note that to rm, mv, or cp directories you need to put "-r" between the command and the file.
So to copy a directory: "cp -r /directory1 /diretory2"

---

### Post by marmiteOlz on 2006-11-07
ok hmm lol im dumb
file i want is in Desktop/downloads/flashfolder
do i need to type sudo mv /username/Desktop/downloads/flashfolder/flashfile /usr/lib/firefox/plugins   

or just (assuming i  cd to the downloads folder)
 sudo mv/flashfolder/flashfile /usr/lib/firefox/plugins

when i tried   it said cannot stat    no such file or folder:-k

---

### Post by marmiteOlz on 2006-11-07
wooohooo i done it
crack open the beer  its party time

i had to use home/username/Desktop  prior to file/folder
while the opening of beer may seem excessive i am actually enjoying 
LEARNING  to do something so simple rather than windows copy n paste
 and thanks for the help:mrgreen:

---

### Post by CatKiller on 2006-11-07
> **marmiteOlz said:**
> it wont let me copy n paste through drag and drop method ( im a noob so i dunno why)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by marmiteOlz on 2006-11-07
thanks for the links ive added them to firefox favourites

---

### Post by Iowan on 2006-11-07
CAREFUL!!! That command-line stuff can get addictive - before long you may prefer it to GUI...

---

### Post by BatteryCell on 2006-11-07
> **Iowan said:**
> CAREFUL!!! That command-line stuff can get addictive - before long you may prefer it to GUI...

Lol sadly this is true...

---

### Post by funrider on 2006-11-07
one suggestion is to understand what "sudo" really means in ubuntu...

---

### Post by bodhi.zazen on 2006-11-07
Here is a link: [basic CLI](http://doc.gwos.org/index.php/CommandLineBeginners)

---

