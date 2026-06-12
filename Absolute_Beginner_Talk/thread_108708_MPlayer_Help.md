---
title: "MPlayer Help"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by Skump on 2005-12-26
i just downloaded Mplayer-1.0pre7try2.tar.bz2 and when i try to configure it so i can run the program it says it cannot find a bunch of files... does anyone know what i need to download to get those files and where i have to put them for MPlayer to detect it? thanks in advance!

---

### Post by endersshadow on 2005-12-26
Please post your output.  Then it will be much easier to decipher your problem.

---

### Post by Skump on 2005-12-26
what is output?

---

### Post by endersshadow on 2005-12-26
It's what your terminal says when you try to compile mplayer.

On that note, why can't you use Synaptic to install mplayer, and why are you trying to compile from source?

---

### Post by Maccabee on 2005-12-26
You would have got an output saying Mplayer depends on this,this ..
Because those library files are probably not installed.So you may need to download each of them separatly to get Mplayer working.You may use apt-get which is much simpler.

---

### Post by Skump on 2005-12-27
============ Checking for cc version ============
Result is: not found

============ Checking for gcc version ============
Result is: not found

thats what i am getting and i don't know what those file mean, i don't have any of the other gcc files either. What is Synaptic?

---

### Post by gsdefender on 2005-12-27
Ubuntu default install lacks the GNU C/C++ compiler. Synaptic is a front end to the Debian package management tools. You'll find it in the System menu of your GNOME installation. You should install the gcc, g++, automake, autoconf packages before trying to compile something.

MPlayer should already be available through Synaptic; if not, you can use Xine, another player that can use MPlayer codecs (if you are on a 32 bit target).

P.S. Don't forget to do an apt-get update before trying to use Synaptic.

---

### Post by Skump on 2005-12-27
[QUOTE=gsdefender]Ubuntu default install lacks the GNU C/C++ compiler. Synaptic is a front end to the Debian package management tools. You'll find it in the System menu of your GNOME installation. You should install the gcc, g++, automake, autoconf packages before trying to compile something.

MPlayer should already be available through Synaptic; if not, you can use Xine, another player that can use MPlayer codecs (if you are on a 32 bit target).

P.S. Don't forget to do an apt-get update before trying to use Synaptic.[/QUOTE]



i have no idea what most of that means, where do i get these files?

---

### Post by rancourt on 2005-12-27
[QUOTE=Skump]i have no idea what most of that means, where do i get these files?[/QUOTE]

You should be able to get the GCC compiler package via Apt, Ubuntu's package management system. From the shell, "sudo apt-get install gcc" should do it.

---

### Post by endersshadow on 2005-12-27
Access Synaptic by going to the System menu, then to Administration, and then to Synaptic Package Manger.

Enjoy.

---

### Post by Maccabee on 2006-01-08
Hmm..
        > i have no idea what most of that means, where do i get these files?

When you first install Ubuntu 5.10 from CD your system lacks some files(Eg. gcc)
That is present on the CD itself but not installed by the default setup.
In short you need to insert the CD inthe drive and open synaptic package manager, then mark those files for installation and then apply it.Those basic file listed are almost necessary for your system and not installed by default is a real annoyance.I suppose I put it right.
Hope you got the ponit abt gcc

---

### Post by mo_x on 2006-01-08
From a terminal window type:
```
sudo apt-get install build-essential libx11-dev libxv-dev
```
You will probably need some more packages but I don't remember them :)
There are a lot of threads on compiling mplayer, search the forum.

---

