---
title: "What is different between executing ./aaa.sh and aaa.sh?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-03-03
Hi
thank you for reading my post.
what is different between executing ./aaaa.sh and aaaa.sh?
I mean what that ./ means?

Thanks

---

### Post by Vadi on 2008-03-03
It means execute the file that is in this current directory. So if aaaa.sh is not in that folder, the command will fail.

aaaa.sh will try and find that script in several known locations (which I think they're defined by the $PATH variable), so it's more "global".

---

### Post by taurus on 2008-03-03
It means the current directory because aaa.sh is not on your path.  If the directory where aaa.sh is located is on your path, then you can just type in the name to execute it.  But if aaa.sh is in a directory that is not on your path, then you need to specify where it is by using the ./, current directory.

---

### Post by lswest on 2008-03-03
"./" tells the bash shell (the command prompt/terminal) that the file you're running is located in the folder you're in at the moment, whereas if you just run the command without it, i believe it implies it is found in the /usr/bin folder or so

---

### Post by BillDozer on 2008-03-03
**aaa.sh** will look in your path and execute the (an executable) script.

**./aaa.sh** will start the script that is in active folder. ./ stands for active folder.

---

### Post by nhandler on 2008-03-03
./aaa.sh is a relative path to the file. In order for that command to work, you must cd into the directory where the script is located. For example, let's say the script is located in /home/username, but my current working directory is only /home. You have a few options for how to execute the script:
1) You can use a relative path: ./username/aaa.sh
2) You can use the absolute path: /home/username/aaa.sh
3) You can sudo cp /home/username/aaa.sh /usr/bin and then execute 'aaa.sh'. This will work from any directory (not recommended).

---

### Post by LarryJ2 on 2008-03-03
If you want to see what directories (folders) are in your "path" enter the command shown below in a terminal session (window) .   Again as described above, these are the directories where the shell (command prompt like program) will look for files.  If  aaaa.sh is in any of them,  the shell will find it and run it if you issue  sh aaaa.sh 

```
$echo $PATH
```

For example,  my laptop with Kubuntu 7.10 produces

> $ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

So if aaaa.sh  is located in the directoyr **/usr/local/sbin**,   **sh aaaa.sh ** will invoke the shell and the shell will attempt to open the file aaaa.sh by looking in each of the directories in your environmental PATH variable.    If aaaa.sh is NOT in any these $PATH directories, then the shell faills to find the  aaaa.sh  and  you are prompted **sh: Can't open aaaa.sh**

What's a Terminal window (terminal session aka command prompt)?  In KDE,  KMenu->System->Konsole  will bring one up on your desktop.

---

### Post by Vadi on 2008-03-03
I believe the OP will surely get it when they check back now ;)

---

