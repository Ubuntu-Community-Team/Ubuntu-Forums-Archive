---
title: "how do u start cpuburn?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2007-03-25
installed cpuburn from the repos. But when i go to the terminal and type cpuburn it tells me the command wasn't found

---

### Post by Kobalt on 2007-03-25
Have you read the README file ? 
>  "./cpuburn-in 10" will run the test for ten minutes.

---

### Post by lime4x4 on 2007-03-25
brain fart here this morning........thanks

---

### Post by jokker on 2008-02-27
./cpuburn-in 10 
bash: ./cpuburn-in: No such file or directory

---

### Post by Oldsoldier2003 on 2008-02-27
> **jokker said:**
> ./cpuburn-in 10 
bash: ./cpuburn-in: No such file or directory
check your path

---

### Post by az on 2008-02-27
[http://packages.ubuntu.com/gutsy/i386/cpuburn/filelist](http://packages.ubuntu.com/gutsy/i386/cpuburn/filelist)

/usr/bin/burnBX
/usr/bin/burnK6
/usr/bin/burnK7
/usr/bin/burnMMX
/usr/bin/burnP5
/usr/bin/burnP6

sudo run it with

burnK7 or burnP6 if you are running a modern computer.

---

### Post by oldb0y on 2008-02-27
I'm just curious, what is this cpuburn?

---

### Post by az on 2008-02-27
CPUburn is a collection of programs to put heavy stress on CPU. These programs are designed to load x86 CPUs as heavily as possible for the purposes of system testing.

Warning: The goal has been to maximize heat production from the CPU, putting stress on the CPU itself, cooling system, motherboard. This may cause data loss (filesystem corruption) and possibly permanent damage to electronic components. Use at your own risk. 

One uses CPUburn to test new hardware or to troubleshoot possible hardware problems.

---

### Post by sayakb on 2008-02-27
Hey hey.. i installed cpuburn.. "Damage to hardware" .. sounds dangerous. Anyway, how do I run it?
I type cpuburn at the terminal and it tells me Invalid command..

Edit: Sorry... I am really dumb you see.. I am reading the thread now.. Ignore this post ..

---

### Post by oldb0y on 2008-02-27
> **az said:**
> CPUburn is a collection of programs to put heavy stress on CPU. These programs are designed to load x86 CPUs as heavily as possible for the purposes of system testing.

Ok. I guess I don't need this.

---

