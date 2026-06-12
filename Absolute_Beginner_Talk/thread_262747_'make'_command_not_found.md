---
title: "'make' command not found"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by penguinKabuki on 2006-09-22
situation: i'm trying to upgrade my gcc from version 2.65 to version      4.02.

i've done:
1) extract the .tar file
2) run the " ./configure " command
3) the problem starts when i try to run " make "

the problem :
when i try to run " make " command, the error was

" bash : make command was not found

then itry to run " make install " instead, still the error was:

* bash : make command was not found

so, i try " ./configure " again, the try reading the " README " n " INSTALL " again, still i can't find the solution.

So, where does " make " come from? From which program? Please help me
TQ in advance.

Btw, i'm using KUbuntu 6.06.
Current GCC version 2.65.

---

### Post by Perfect Storm on 2006-09-22
Are you sure? Gcc v. 4.0.3 is in the repo.

---

### Post by chrisfay on 2006-09-22
```
sudo apt-get install make
```

or

```
sudo apt-get install build-essential
```

---

### Post by penguinKabuki on 2006-09-22
yup

at first, i try to install Mplayer.

the, at "./configure", the Mplayer error was

We don't support gcc 2.65 and below.
( sumthing like this )

that's is why i try to upgrade to 4.02..

nway, where's the repo that contains gcc 4.03?

forgive my noobness. TQ in advance.

---

### Post by Average Joe on 2006-09-22
When use do:
```
sudo apt-get gcc
```
You probably get the lastest version of the c compiler. But actually, I would do as chrisfay suggested and do:
```
sudo apt-get install build-essential
```
That will give you all the latest necessary tools to compile your stuff.

---

### Post by 3rdalbum on 2006-09-22
Type:

```
gksudo gedit "/etc/apt/sources.list"
```

Now uncomment all the lines that begin with "deb" or "deb-src". (when I say "uncomment", I mean get rid of the # symbol before them.

Save your changes, exit Gedit, and type the following into the terminal:

```
sudo apt-get update
sudo apt-get install mplayer
```

---

### Post by penguinKabuki on 2006-09-22
penguin@penguin-desktop:~/Desktop/gcc-4.0.2$ gksudo gedit "/etc/apt/sources.list"
bash: gksudo: command not found

:(

---

### Post by CatKiller on 2006-09-22
I believe that the command for Kubuntu would be ```
kdesu kate /etc/apt/sources.list
```

No quotes. Why not use Synaptic?

---

### Post by penguinKabuki on 2006-09-22
thanks all people.
after using this distro since it being distribute...
i cannot do anything because my university management really sucks.
they blok a lot of thing.
n...now...im going to shut down my computer...and install the damm windows back into my box~

thx all~~~

---

