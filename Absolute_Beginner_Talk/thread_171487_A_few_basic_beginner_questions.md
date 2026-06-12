---
title: "A few basic beginner questions?"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by whoamthis on 2006-05-06
What is a command for running a file from the terminal?
what is the command for opening a terminal in a terminal?
What C++, and java editors will be the best to use?
How can i install wine? {
I tried doint sudo apt-get install wine, but that didnt work 

this is what happens
arit@ubuntu-imput:~/Desktop $ sudo apt-get install wine
Reading Package Lists... Done
Building Dependency Tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) wine/sourceforge Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_dists_wine_sourceforge_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) wine/wime Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_dists_wine_wime_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package wine has no installation candidate

---

### Post by Omnios on 2006-05-06
To open a text file type sudo gedit /Directories/file-name to edit a file in root or without sudo for normal user. Most executable can be run by putting a period in fornt of them ex .nwn or ./nwn, There is a forum post link in my signature with terminal commands with some for referene, some are tutorials etc. Personaly I got the ubuntu wine from I think it was universe which worked rather well. And sudo apt-get update updates your repsoity list for synaptic.

---

### Post by user1397 on 2006-05-06
[quote=whoamthis]
this is what happens
arit@ubuntu-imput:~/Desktop $ sudo apt-get install wine
Reading Package Lists... Done
Building Dependency Tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://wine.sourceforge.net]("http://wine.sourceforge.net") wine/sourceforge Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_dists_wine_sourceforge_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net]("http://wine.sourceforge.net") wine/wime Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_dists_wine_wime_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package wine has no installation candidate[/quote]
First type in the terminal: 
```
sudo apt-get update
```
then do ```
sudo apt-get install wine
```

---

### Post by Sef on 2006-05-06
> What is a command for running a file from the terminal?

Do you mean starting a program from the terminal? (rhythmbox, firestarter, etc.)

> what is the command for opening a terminal in a terminal?

Do you mean like File > New in Gnome-Terminal?

> What C++, and java editors will be the best to use? 

To compile you need build-essential.

sudo apt-get update

sudo apt-get install build-essential

> How can i install wine? {
I tried doint sudo apt-get install wine, but that didnt work

You need to turn on multiverse and universe in the repositories.  Click on the link below to read how to do it.

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

Note: I believe wine is in Universe.

---

### Post by htinn on 2006-05-06
#1:
```
exec [-cl] [-a name] file [redirection ...]
```

#2: (these are just three popular ones):
```
gnome-terminal
konsole
xterm
```

#3: I like Anjuta for C++ although there is also KDevelop or Eclipse, etc.

#4: Wine should be available in the "Universe" repo. See this if you need help on that:

[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)

EDIT: See erik1397's post above. This is why I hate typing replies for 5 minutes. :p

---

### Post by whoamthis on 2006-05-06
thanks a lot, you all we great help

---

