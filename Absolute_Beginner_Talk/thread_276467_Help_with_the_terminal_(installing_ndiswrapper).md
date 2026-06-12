---
title: "Help with the terminal (installing ndiswrapper)"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by unrealmstr on 2006-10-12
Ok so im really confused about how to use the terminal. I have downloaded the ndiswrapper-1.25.tar.gz and this is what I do (I run it in terminal)
```
cd Desktop
``` (i put it on my desktop)
```
tar -zxvf ndiswrapper-1.25.tar.gz 
```
```
cd ndiswrapper-1.25
```
and here is what im stuck on, it tells me to type
```
make
make install
```
i do this and it says its an unreconized command. all help is appreciated, and keep in mind im retarded with linux obviously :(

---

### Post by aysiu on 2006-10-12
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by unrealmstr on 2006-10-12
I dont have the internet thats why im installing ndiswrapper so I can use a windows driver for my WMP54G wireless card :(

---

### Post by aysiu on 2006-10-13
Okay.

That's why I gave you that first command: ```
sudo apt-cdrom add
``` It adds the CD as a repository source (so you won't need the internet to get *build-essential*).

---

### Post by unrealmstr on 2006-10-13
so I put ndiswrapper on the CD? please explain
edit: or do i put in the ubuntu install CD?

---

### Post by aysiu on 2006-10-13
When you install software with the package manager, it looks for repositories or "sources" for software.

Usually, the sources are online ([http://archive.ubuntu.com](http://archive.ubuntu.com), for example), but since you don't have an internet connection, you're going to be using your Ubuntu CD as a source.

Ubuntu, for some strange reason, doesn't come with the *make* command. That's why when you tried to compile *ndiswrapper*, you were told *bash: make command not found*.

So you need to install *make* and all the other compiling tools: ```
sudo apt-cdrom add
``` This command tells Ubuntu to use the installer CD as a software source or repository ```
sudo aptitude update
``` This command refreshes for the package manager the list of what software is available. ```
sudo aptitude install build-essential
``` This installs all the tools you need to compile *ndiswrapper*.

---

### Post by unrealmstr on 2006-10-13
Thank you for the help, I figured it out sorry for appearing so stupid, I have installed binutils and ran "make" in the directory ndisswrapper-1.25 and it says:
```
root@unrealmstr:~/Desktop/ndiswrapper-1.25# make
make -C driver
make[1]: Entering directory `/root/Desktop/ndiswrapper-1.25/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/root/Desktop/ndiswrapper-1.25/driver'
make: *** [all] Error 2

```
also when i try to install my NVIDIA drivers it says i am running X server and i need to exit how do i do that

---

### Post by aysiu on 2006-10-13
That goes a bit beyond my knowledge. I know you need to install *build-essential*, but I've never used *ndiswrapper* before.

I don't see why NVidia drivers would need you to exit the X server, but you can try this: ```
sudo /etc/init.d/gdm stop
```

---

### Post by unrealmstr on 2006-10-13
ok whats the command to run a *.run file from terminal?

---

### Post by aysiu on 2006-10-13
Let's say it's *program.run*

I think it's ```
sudo chmod +x program.run
sudo ./program.run
```

---

### Post by unrealmstr on 2006-10-13
well ndiswrapper needs the "kernal build files"... any help is appreciated

---

