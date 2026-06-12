---
title: "all programs just got uninstalled"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2007-03-17
I was going to install a program and ran the ./configure to notice that I was missing a library so I figured I would try to install with aptitude since I read that it would install all the necessary libraries for you. 

So I ran the command sudo aptitude install (this is obviously wrong) then got a prompt to remove a couple libraries, which is something else that aptitude is supposed to manage well, then all of a sudden it was removing ALL my friggin libraries.  I now can't run to much videos, mp3's, mysql etc.

It seems that it didn't recognize that programs did use those libraries and then trashed them.  Is there any quick recovery method for this, besides turning to the dark side and getting a mac? (I know I can reinstall all the libraries manually, but it sickens me that it is that easy to screw up a nicely set up system.

Thanks

---

### Post by bapoumba on 2007-03-17
Could you check if ubuntu-desktop is still installed ?
```
aptitude show ubuntu-desktop
```
If not, reinstall it with aptitude:
```
sudo aptitude install ubuntu-desktop
```
Aptitude relies on its own log file to check if packages are dependencies in use. But it also should prompt you and give every package name that gets to be removed.

---

### Post by ComplexNumber on 2007-03-17
> **chris.olsen said:**
> I was going to install a program and ran the ./configure to notice that I was missing a library so I figured I would try to install with aptitude since I read that it would install all the necessary libraries for you. 

So I ran the command sudo aptitude install (this is obviously wrong) then got a prompt to remove a couple libraries, which is something else that aptitude is supposed to manage well, then all of a sudden it was removing ALL my friggin libraries.  I now can't run to much videos, mp3's, mysql etc.

It seems that it didn't recognize that programs did use those libraries and then trashed them.  Is there any quick recovery method for this, besides turning to the dark side and getting a mac? (I know I can reinstall all the libraries manually, but it sickens me that it is that easy to screw up a nicely set up system.

Thanks
when running configure scripts, you need to have the "dev" packages installed. for example, if you have gtk2.0 installed but don't have the gtk2.0-dev package installed, the configure script will believe that you don't have gtk2.0 installed.

the reason why it was removing many of your libraries is probably because the program that you were trying to install depended upon older or newer versions of all those libraries that aren't available in the repos, so thats why it probably tried to uninstall them.

---

### Post by chris.olsen on 2007-03-18
there were no problems with the ubuntu-desktop, and I got everything back up and working (it wasn't as bad as I first thought)

as for the dev files that was the reason ./configure gave me the message, but that was no big deal, it was the fact that a number of libraries were removed after running the aptitude install command.  I got a few of the ones that I noticed re-installed through aptitude and chances are there a few more that I don't know of, but I will get to that when the time comes.

Thanks for the help.

---

