---
title: "I have downloaded realplayer.bin"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by fedrik on 2007-08-08
but How do I install it???

I am using kubuntu. 

thanks in advance

---

### Post by Outrunner on 2007-08-08
Go to the terminal (Konsole on Kubuntu) and type

```
/path/to/filename.bin
```

so if your file in on your Desktop, that would be

```
~/Desktop/realplayer.bin
```

---

### Post by dreadlord_chris on 2007-08-08
just run it...
if it's on your Desktop - double-click it
if it's elsewhere:
```

/path/to/realplayer.bin

```

---

### Post by cawill on 2007-08-08
Open terminal (konsole) up in the directory you have realplayer.bin (or whatever its called), then type 'sudo ./realplayer.bin' (change realplayer.bin to the correct filename).

---

### Post by fedrik on 2007-08-08
I am getting...

__________________________________________________________________
mypc@mypc:~/Desktop$ sudo ./RealPlayer10GOLD.bin
Password:
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
mypc@mypc:~/Desktop$

__________________________________________________________________

What's wrong with it??

---

### Post by Hospadar on 2007-08-08
try doing ```
sudo apt-get install build-essential
``` this will install all the standard c libraries and such.  hopefully that will work for you.

---

### Post by igknighted on 2007-08-08
You are making this way harder than it should be...

Step 1) Delete that file.

Step 2) Type this line in the terminal: ```
kdesu kate /etc/apt/sources.list
```  Note: If kdesu does not work for some reason, try sudo instead.

Step 3) Add this line to the bottom of the file: ```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

Step 4) Save and exit the file.

Step 5) Open Adept Package Manager.

Step 6) Click Update/Reload whatever the button is.

Step 7) Search (still in Adept) for realplayer

Step 8) Select it and click install

Now if there are updates to real player you will get them automatically, plus it will download any dependencies you need (like the C libraries) and make the install much easier.

EDIT: Updated for Kubuntu apps.

---

### Post by Hendrixski on 2007-08-08
Isn't realplayer in the repositories?  That would be way easier than downloading all the build-dependancies for it and then compiling.  Unless you want to learn from doing that, in which case knock yourself out.

---

### Post by Rul on 2007-08-08
Check out this webpage it will help you to install most of the applications you may want[http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

---

