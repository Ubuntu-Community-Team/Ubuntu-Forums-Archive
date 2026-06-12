---
title: "keep screwing up!"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by edwardzafra on 2006-05-27
W: Couldn't stat source package list cdrom://Ubuntu 5.10/_Breezy Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_%5fBreezy_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/Badger_ Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_Badger%5f_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/- Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_-_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/Release Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_Release_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/powerpc Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_powerpc_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/(20051012)]/ Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_(20051012)%5d__binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/breezy Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_breezy_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/main Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10/restricted Packages (/var/lib/apt/lists/Ubuntu_dists_5.10_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)


Man, why me!

---

### Post by localzuk on 2006-05-27
Hi, Could you post the contents of your /etc/apt/sources.list here?

---

### Post by edwardzafra on 2006-05-27
whats the command for that agian ?

---

### Post by uzi09 on 2006-05-27
gedit /etc/apt/sources.list

then copy paste everything here :D

ps: what ubuntu are u using?
type: lsb_release -a
to find out

---

### Post by ProjectGod on 2006-05-27
hello edward,

hows the ubuntu battle going? :mrgreen:

follow this thread and download the attachment. don't unzip it. just rename it to source.list... and replace your current source.list.

theyre just multiverse / universe enabled. nothing else. no nasty scripts or anything else. :D

[http://www.ubuntuforums.org/showthread.php?t=183377](http://www.ubuntuforums.org/showthread.php?t=183377)

OR you could follow the guide

[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28adding%29%7C%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28adding%29%7C%28repositories%29)

---

### Post by edwardzafra on 2006-05-27
Linux Appoloin 2.6.12-10-powerpc #1 Fri Apr 28 13:22:38 UTC 2006 ppc GNU/Linux

i have downloaded the zip file and its on my desktop..2 things.

how do i rename it?
where do i save it?

sorry for the dumb questions

---

### Post by ProjectGod on 2006-05-27
right click on it. and select "rename"

then rename it to "sources.list" (without the quotation marks of course!)

now open the terminal again... type

**cd /etc/apt/**
then type

**sudo rm sources.list**
enter YOUR password

then go back to GUI... right click on the sources.list you've just renamed and select CUT... browse to etc/apt from your my computer... and paste it into this directory...

whammy your done!

then go back to terminal and type:

**sudo apt-get update**

and it should work!

---

### Post by ProjectGod on 2006-05-27
by the way edward. you should really check out these two links. excellent for the n3w81e ... newbie. :D

[http://www.ubuntuguide.org](http://www.ubuntuguide.org) (no beating around the bush guide acts as a quick reference 4/5 stars)

[http://linuxnewbieguide.org/](http://linuxnewbieguide.org/) (this one is excellent beyond words! 5/5 stars!!!) :mrgreen:

---

### Post by edwardzafra on 2006-05-27
projectgod.. im using a powerbook.. no right click.. other wise i would have work that out

---

### Post by uzi09 on 2006-05-27
[QUOTE=laix1234]catlett, i tried that and still no sound....

nudnik, i believe i mean 5.10, is there an easy way to tell?  i tried the restricted format stuff, but with no luck.  it did what it was supposed to do, but still no sound... 

based solely on what i've been reading, could it be a problem with my soundcard not being recognized, and if so how would i tell?




p.s.  thanks again for everyone's help, it's amazing how fast people who are under no obligation reply to help you on this forum...[/QUOTE]

lol, try this (lousy macs :P)
```

sudo mv ~/sources.list.zip /etc/apt/sources.list

```
(replace ~/ with whatever directory you downloaded the sources.list file, and replace the name with the correct name, sorry, i don't remember what it was)


ps: as far as how helping everyone is -- that's Ubuntu support for yah :D

---

### Post by edwardzafra on 2006-05-27
vlad@Appoloin:~$ sudo mv desktop/sources.zip /etc/apt/sources.lis

this right?

---

### Post by uzi09 on 2006-05-27
> 
vlad@Appoloin:~$ sudo mv desktop/sources.zip /etc/apt/sources.lis


don't for get the 't' at the end!

---

### Post by edwardzafra on 2006-05-27
vlad@Appoloin:~$  sudo mv desktop/sources.zip /etc/apt/sources.list
mv: cannot stat `desktop/sources.zip': No such file or directory

i save it on my desktop

---

### Post by uzi09 on 2006-05-27
lol edward, we seem to be going back and forth. if you have msn, do you mind if i add you? i can help you using remote desktop if you'd like!

go ahead and pm me your info if you don't mind...otherwise try this:

```

sudo mv ~/Desktop/sources.zip /etc/apt/sources.list

```

make sure you have caps on in the right places!

---

### Post by edwardzafra on 2006-05-27
i guess that work.. but where did the list go? its not on my desktop now.

---

### Post by uzi09 on 2006-05-27
mv = MOVE

if you'd like a copy on your desktop, you can always copy it back with this:
```

cp /etc/atp/sources.list ~/Desktop/

```

also, why don't you try to update and upgrade at this point?
```

sudo aptitude update
sudo aptitude upgrade

```

---

