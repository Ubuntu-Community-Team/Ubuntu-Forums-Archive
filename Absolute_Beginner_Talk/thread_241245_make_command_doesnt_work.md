---
title: "make command doesnt work"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by ezek on 2006-08-22
Hey, when im trying to install a program i cant use the make command after the cd <filename> command.
whenever i do the make command after it cant find something it just says **bash: make: command not found**

---

### Post by aysiu on 2006-08-22
```
sudo aptitude update && sudo aptitude install build-essential
``` then try again.

---

### Post by Josh_b on 2006-08-22
I'm not 100% sure, but I thought the code to make a new dir was ```
mkdir <path-filename>
```
I may be wrong.

---

### Post by aysiu on 2006-08-22
That is the command to make a new directory, but ezek isn't trying to make a new directory.

---

### Post by ezek on 2006-08-22
How can i update those? i cant see any updated versions in manager

---

### Post by aysiu on 2006-08-22
> **ezek said:**
> How can i update those? i cant see any updated versions in manager
What are you trying to update?

---

### Post by ezek on 2006-08-22
the sudo aptitude thing you said

---

### Post by atomkarinca on 2006-08-22
you can just "sudo apt-get install make" and then use the make command.

---

### Post by aysiu on 2006-08-22
> **ezek said:**
> the sudo aptitude thing you said
Just paste the command I gave you into the terminal. If there are any errors, post them back here.

---

### Post by ezek on 2006-08-22
alright, it worked, 1 more question. I can get Azureus to work though terminal but i cant get a desktop icon to open it up. Can i get some help?

---

### Post by aysiu on 2006-08-22
Right-click on the desktop and create a launcher.

For the command, put the command you'd normally put in the terminal to launch it (I'm assuming it's *azureus*).

---

### Post by ezek on 2006-08-22
I got into azureus by not installing it, do i need to install it? i do cd <file> and then sudo apt-get install <file> but it says it cant find the package and when i use make it says that i need to specify what to make

---

### Post by aysiu on 2006-08-22
You need extra repositories in order to install Azureus with *aptitude* or Synaptic (there's no reason to use *apt-get*--if you're using the command-line anyway, might as well use *aptitude*):
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

You can add extra repositories...
**graphically**: [http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)
**by command-line**: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

After that, just do ```
sudo aptitude update && sudo aptitude install azureus
``` and you're on your way.

P.S. In the future, you should post what you're trying to do in addition to what the obstacle you're facing is. For example > I'm trying to install Azureus from a .tar.gz and I can't get the *make* command to work To which you would probably get the reply right away > Why are you installing Azureus from source? It's in the Universe repositories. Here's how to install it...

---

