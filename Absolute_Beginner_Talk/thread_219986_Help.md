---
title: "Help"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Goemon4 on 2006-07-20
ok i need to replace my sources.list file in the /etc/apt folder with a new one...how can i replace the old one with a new one that i made? 



btw im on a ppc mac runnin ubuntu 6.06

thanks
-Goemon4

---

### Post by catlett on 2006-07-20
First back up your old list just in case
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
Then enter this to open the document
```
sudo gedit /etc/apt/sources.list 
```Erase what is in there and copy your list in. Make sure to save the file.
Then run ```
sudo apt-get update
```to update the list. You can then open synaptic and browse for applications or install with apt-get if you know exactly what you want.

---

### Post by kingmonkey on 2006-07-20
Are you sure you know what your doing? Im not going to tell you how because its dagerous to do and it doesnt really sould like you know what your doing. Type these into a terminal and it will give you a big pointer

```
$ man sudo 
```
```
$ man cp 
```

---

### Post by Goemon4 on 2006-07-20
thanks, ill try that now

also im not a total n00b, ive been running ubuntu 5.10 for a while on my old dell and know my way around it...for some reason i just cant over write this file (cause ive never messed with system files) i did that with osx 10.3 and got a kernel panic (long story short i was replacing files and it happened) so i know what im doing (for the most part) but i haven used linux in a while so i forgot what to do ](*,) 

also that worked thanks that worked

---

### Post by kingmonkey on 2006-07-20
Sorry, wanst calling you a n00b, just didnt want to be blamed if it all went wrong.

You need to be superuser to change system files by using "sudo".

---

### Post by catlett on 2006-07-20
> **kingmonkey said:**
> Are you sure you know what your doing? Im not going to tell you how because its dagerous to do and it doesnt really sould like you know what your doing. Type these into a terminal and it will give you a big pointer

```
$ man sudo 
```
```
$ man cp 
```

THat is why the first command is there. He is cp-ing the list to /etc/apt/sources.list_backup. If there is an issue he can replace it. I gues I should have added this part
If something goes wrong, you can get your old list back with this command 
```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
```

---

### Post by Goemon4 on 2006-07-20
everything went well thanks for all the help, but i came across another problem with the terminal...im trying to run an installer and when i type ./*installername* it says no such file or directory...when i realised my directory was wrong i typed cd / then cd desktop and it said no such file or directory....why is the terminal doing this? is it a bug or am i just doing something wrong? bty im not logged in as root (though i doubt that is the problem) but i am able to run apps from the terminal (like dosbox and such) 

plz help

---

### Post by catlett on 2006-07-20
I'll give you my cd trick. It can be a pain writing in the correct path to a folder or file. Tab completion works god but it still takes effort. :-D 
What I do, is utilise drag and drop. Open the terminal and enter cd. Then press spce so the next entry doesn't follow right after cd bt has a space between d and the next thing.
Now drag the folder, directory that you want to be in into the terminal and drop. When you drop it, it will print out the path to the folder in the terminal. Just press enter and you are there.
So in this case drag the folder that the installer script is in into the tewrminal. Press enter and you are in the folder with the installer. Now run the ./.
Another good thing to do is use tab completion when you finally run the command. Enter ./ins then press tab. It will complete the file name if it exists in the directory your in. That way you know it is the correct entry.

P.S. desktop is with a capital D
```
cd Desktop
```

---

### Post by Goemon4 on 2006-07-21
thanks alot, ill try that now, also one last thing, will these installers work on a ppc mac ?

[http://www.liflg.org/?catid=1](http://www.liflg.org/?catid=1)

i know some use wine (which i know is x86 only) but what about the others?

---

