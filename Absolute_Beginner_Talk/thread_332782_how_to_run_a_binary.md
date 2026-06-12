---
title: "how to run a binary ?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-06
I have downloaded a certain binary installer ( NetBeans IDE ) for Linux,  since i couldn't find the program in the repository. How can i run *.bin
I tryed :
```

sasa@Kanta:~/Desktop$ netbeans-5_5-linux.bin
bash: netbeans-5_5-linux.bin: command not found
sasa@Kanta:~/Desktop$ 

```

PS : i have chmod the file to a+x

---

### Post by Bachstelze on 2007-01-06
try 

```
./netbeans-5_5-linux.bin
```

If it's an installer, you'll most certainly need sudo too.

---

### Post by Sasa_Ivanovic on 2007-01-06
It works! But what diffrence does it make ? I don't understand this ...

---

### Post by taurus on 2007-01-06
> **Sasa_Ivanovic said:**
> It works! But what diffrence does it make ? I don't understand this ...

Since ~/Desktop is not in your path, it can't find netbeans-5_5-linux.bin!  Therefore, you need to specify where it is and ./ means current directory!!!

---

### Post by Bachstelze on 2007-01-06
In Unix-like systems, . means the current directory, for example :

```
cp /etc/apt/sources.list .
```

would make a copy of your sources.list in the current dir. But when you type just a command, for example *cp*, you don't have the cp executable in your current dir, do you ? Instead, the shell will look for it in the directories appearing in your $PATH (you can see which ones by doing *echo $PATH*).

SO, to make the shell understand the executable you want to run is in the current dir, and not in the $PATH, you add ./ - you could as well have done *Desktop/netbeans-5_5-linux.bin* without leaving your home dir, or */home/sasa/Desktop/netbeans-5_5-linux.bin* from any dir in the system.


Note this is only needed for executables, you can omit it if you just want to read a file, for example

```
nano ./foobar.txt
```

is the same as

```
nano foobar.txt
```

---

### Post by Sasa_Ivanovic on 2007-01-06
that is the strange part. I was used to relative path when using commands. Now when i have to start a binary i have to provide the apsolute path...

whatever, netbeans works very well.

I have another question though :
When you need some app or game is the binary same for all distros of Linux.

---

### Post by taurus on 2007-01-06
> **Sasa_Ivanovic said:**
> that is the strange part. I was used to relative path when using commands. Now when i have to start a binary i have to provide the apsolute path...

Because those commands are already in your PATH--/bin, /usr/bin, etc.!!!  


> When you need some app or game is the binary same for all distros of Linux.

It depends on what they are.  Sometimes you need to have the libraries to run them so before you install it, you can check with

```
file **filename**
```

---

### Post by Sasa_Ivanovic on 2007-01-06
How can i edit this mistirous PATH variable ?

---

### Post by Bachstelze on 2007-01-06
> **Sasa_Ivanovic said:**
> that is the strange part. I was used to relative path when using commands. Now when i have to start a binary i have to provide the apsolute path...

No, you don't :) *./foobar* is not an absolute path since it doesn't start with a / - it's a relative path to the current dir. The absolute path is the complete path to the file, from the filesystem's root, in your case it would be */home/sasa/Desktop/filename.bin*.

Editing the PATH variable is not a goot idea, security-wise. It's usually better to make a symlink to the file in /usr/local/bin - or any other dir in the path but i's the most commonly used.

---

### Post by taurus on 2007-01-06
```
gedit ~/.bashrc
```
Then add

```
PATH=$PATH:**new_path**:**more_new_path**
export PATH
```

---

### Post by Sasa_Ivanovic on 2007-01-06
> **HymnToLife said:**
> No, you don't :) *./foobar* is not an absolute path since it doesn't start with a / - it's a relative path to the current dir.
No it isn't.
Let's say you are in your home dir :
/home/user
the . will represent "/home/user"
and if you do ./file, the shell translates it to "/home/user/file" so in the end it's an apsolute path.

Also when i said that i use commands in relative paths i meant that the files i operate on are relative. Not the commands them self.

](*,)

---

### Post by dannystaple on 2007-01-06
Yes that is correct. Files you operate on are relative, but binaries (or scripts) being run require a path that can be mapped to an absolute path. I would suspect that this was a decision made back in the distance history of *n*x to do with security.

---

### Post by Bachstelze on 2007-01-06
An absolute path is a path that will lead to the same file, regardless of the directory you're in, which is the case with */home/user/foobar*. However, *./foobar* will behave differently depending on the current dir. That makes it a relative path, period.

---

### Post by seijuro on 2007-01-06
if you don't want to include a path for the binary just make a symbolic link to the binary in your /usr/bin directory then all you have to do is type the name of the link from then on

example:
```
/usr/bin$ sudo ln -s /home/sejuro/netbeans.bin ./beans
```

after that you mearly type beans from now on at the command line to run the program.

---

