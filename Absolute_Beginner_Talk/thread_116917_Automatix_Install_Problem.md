---
title: "Automatix Install Problem"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by jimmp226 on 2006-01-13
I have Installed this program 1 time before and everything worked fine. This time when I enter :

wget [http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb)
sudo dpkg -i automatix-ubuntu_4.4-2_i386.deb

into the terminl. This is what happens next :

james@ubuntu:~$ wget [http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb)
--17:34:18--  [http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb)
           => `automatix-ubuntu_4.4-2_i386.deb.2'
Resolving beerorkid.com... 205.196.218.206
Connecting to beerorkid.com|205.196.218.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32,334 (32K) [text/plain]

100%[====================================>] 32,334        86.58K/s

17:34:24 (86.34 KB/s) - `automatix-ubuntu_4.4-2_i386.deb.2' saved [32334/32334]

james@ubuntu:~$ sudo dpkg -i automatix-ubuntu_4.4-2_i386.deb
(Reading database ... 59145 files and directories currently installed.)
Preparing to replace automatix 4.4-2 (using automatix-ubuntu_4.4-2_i386.deb) ...Unpacking replacement automatix ...
Setting up automatix (4.4-2) ...
james@ubuntu:~$
  

 Thats everything on the terminal after I try to install this program. Any ideas. I dont have any idea what any of that means (lol). So any help would be appericiated. Jim

---

### Post by Zimmer on 2006-01-13
[QUOTE=jimmp226]
Resolving beerorkid.com... 205.196.218.206
Connecting to beerorkid.com|205.196.218.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32,334 (32K) [text/plain]

100%[====================================>] 32,334        86.58K/s

17:34:24 (86.34 KB/s) - `automatix-ubuntu_4.4-2_i386.deb.2' saved [32334/32334]

james@ubuntu:~$ sudo dpkg -i automatix-ubuntu_4.4-2_i386.deb
(Reading database ... 59145 files and directories currently installed.)
Preparing to replace automatix 4.4-2 (using automatix-ubuntu_4.4-2_i386.deb) ...Unpacking replacement automatix ...
Setting up automatix (4.4-2) ...
james@ubuntu:~$
  

 Thats everything on the terminal after I try to install this program. Any ideas. I dont have any idea what any of that means (lol). So any help would be appericiated. Jim[/QUOTE]
Looks like it has installed Automatix...control has returned to the Terminal prompt...
Automatix gets installed in Applications--> System Tools

If you have a further problem I suggest you post here:-
[http://www.ubuntuforums.org/showthread.php?t=66563](http://www.ubuntuforums.org/showthread.php?t=66563)
Regards

---

### Post by jimmp226 on 2006-01-13
OK but if I enter:

cat $HOME/automatix.log

I get this as a responce in the terminal:

james@ubuntu:~$ cat $HOME/automatix.log
cat: /home/james/automatix.log: No such file or directory
james@ubuntu:~$


This is saying that it's not installed I belive. Any other ideas. Thanks. Jim

---

### Post by mustang on 2006-01-14
[QUOTE=jimmp226]OK but if I enter:

cat $HOME/automatix.log

I get this as a responce in the terminal:

james@ubuntu:~$ cat $HOME/automatix.log
cat: /home/james/automatix.log: No such file or directory
james@ubuntu:~$


This is saying that it's not installed I belive. Any other ideas. Thanks. Jim[/QUOTE]

Your first post does not show any errors in the installation procedure. 

In the post quoted above, you are trying to view automatix.log, a logfile that shows everything you installed with automatix. Now I may be incorrect but that log file is only generated if you have actually installed something through Automatix.

To use automatix, open the terminal and type "automatix"

edit: sorry, Automatix

---

### Post by arnieboy on 2006-01-14
[QUOTE=mustang]To use automatix, open the terminal and type "automatix"[/QUOTE]
To use automatix, run it from applications --> system tools 
or from terminal as:
```
Automatix
```

---

### Post by jimmp226 on 2006-01-14
If I type "automatix" in the terminal I get this reply:"command not found". Any other ideas? Thanks. Jim

---

### Post by arnieboy on 2006-01-14
[QUOTE=jimmp226]If I type "automatix" in the terminal I get this reply:"command not found". Any other ideas? Thanks. Jim[/QUOTE]
[SIZE="4"]**APPLICATIONS -->SYSTEM TOOLS --> AUTOMATIX**[/SIZE]

---

### Post by sesstreets on 2006-01-14
[size="7"]lol[/size]

---

