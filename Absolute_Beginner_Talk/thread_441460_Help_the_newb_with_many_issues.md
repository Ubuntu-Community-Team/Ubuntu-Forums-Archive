---
title: "Help the newb with many issues"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by tuatha1337 on 2007-05-12
Hello all. I'm a user only a few days exposed to Ubuntu, and Linux in general, so far I like it a lot. It recognized my modem without any hitch or questions asked (unlike my expired Windows, hehe), among other cool things.

So here's the story, I started out with Ubuntu 6.06 Dapper Drake, then upgraded to Edgy Eft, then to Feisty Fawn, and then Kubuntu Feisty Fawn (I was never a fan of the Mac-like desktop). Since the start I've been keeping an eye out for stuff I can't figure out, even searching through these forums, so I'm hoping you guys can help. 

I can't input my password in Terminal. When I try to run commands in Terminal and it asks me for my password, but when I begin typing where the black, blinking box is nothing happens, so I try typing the password anyways thinking maybe it's just hidden. Still no. Any ideas what's going on here?

There were options under windows which I would think were pretty essential to the health of my system, namely defragmentating and error checking the hard drive(s) (among other hard drive stuff like viewing size, format, etc.), viewing running processes, memory usage, and the like. Is there an equivalent to this with Kubuntu? I understand it's most likely command line, which I'm more than willing to learn, but if command line is the answer, where do I learn?

Where do I get codecs to view mp3 files, or at least a program that will convert them to something I can use? Also codecs for Quicktime (if any), flash, and the like?

Azureus! I was always a big fan of the Azureus torrent client. However, Azureus is having issues. It'll shut down somewhat randomly (it takes a few hours) and complain that it was not closed tidily on restarting. Azureus also has a problem with memory usage, After some amount of time it will claim it has a "Disk Read Error - Out Of Memory Error". Any ideas?

I'm sure I'll have more issues in the future, but this is all I can think of for now. If you guys can help that would be great! Thank you much. :biggrin:

---

### Post by drs305 on 2007-05-12
Welcome.

For the first two questions:

1. You won't see anything as you type the password but it is being entered. Type and hit enter. If you've entered the correct password you will be rewarded.   :)  If you've done that, you should get it to work or an error message when you hit enter. 

2. Defragging linux isn't as necessary as with windows. You can search the Ubuntu forums for the technical reasons.

---

### Post by jfinkels on 2007-05-12
> **tuatha1337 said:**
> 
I can't input my password in Terminal. When I try to run commands in Terminal and it asks me for my password, but when I begin typing where the black, blinking box is nothing happens, so I try typing the password anyways thinking maybe it's just hidden. Still no. Any ideas what's going on here?

It's supposed to do that. Just trust that you're password is being put in :D Type it and press enter and it should be fine.

> 
There were options under windows which I would think were pretty essential to the health of my system, namely defragmentating and error checking the hard drive(s) (among other hard drive stuff like viewing size, format, etc.), viewing running processes, memory usage, and the like. Is there an equivalent to this with Kubuntu? I understand it's most likely command line, which I'm more than willing to learn, but if command line is the answer, where do I learn?


You don't need to defragment on Linux, see here for more info on that: [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

View running processes with the program 'top'. Type in the terminal```
top
``` and press q to quit when you're done. Read more in the man pages:```
man top
```

> 
Where do I get codecs to view mp3 files, or at least a program that will convert them to something I can use? Also codecs for Quicktime (if any), flash, and the like?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
> 
Azureus! I was always a big fan of the Azureus torrent client. However, Azureus is having issues. It'll shut down somewhat randomly (it takes a few hours) and complain that it was not closed tidily on restarting. Azureus also has a problem with memory usage, After some amount of time it will claim it has a "Disk Read Error - Out Of Memory Error". Any ideas?


Try opening azureus from the command line by typing the following:
```
azureus
```
And tell us what kind of error messages you get. There are plenty of other torrent clients if azureus turns out to be a hassle for you.

---

### Post by st33med on 2007-05-12
> **drs305 said:**
> Welcome.
2. Defragging linux isn't as necessary as with windows. You can search the Ubuntu forums for the technical reasons.

So true. ext3's journalizing feature saves time. No need to have the OS procrastinate (or not do it at all) and sort it out, it does it immediately.

---

### Post by tuatha1337 on 2007-05-12
Awesome half my problems already solved with simple answers. hehe. Turns out the password is indeed hidden, I was inputting the password wrong. Now I understand why defragging is unessential.

When typing azureus into the terminal I get this
```
The program 'azureus' is currently not installed.  You can install it by typing:
sudo apt-get install azureus
Make sure you have the 'universe' component enabled
bash: azureus: command not found
```
But I know that it is indeed installed as I have a working link to it on my desktop. Maybe it's the location which the program is at? I remembering downloading it once to the "tmp" folder because that was the default, but it disappeared the next day. So I put it somewhere else.

---

### Post by Happy_Man on 2007-05-12
Just to be safe, run 
```
sudo apt-get install azureus
``` 
again. But that really should work.... odd.

---

### Post by tuatha1337 on 2007-05-12
```
linux@Linux-desktop:~$ sudo apt-get install azureus
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package azureus
```

---

### Post by Happy_Man on 2007-05-12
Did you enable the universe repos? Post the output of 
```
cat /etc/apt/sources.lst
```

Sorry if all this code is overwhelming you, but it's a lot easier for us this way than using a GUI-based fix method. I really feel sorry for Dell tech support..."OK, ma'am, could you please open up Add/Remove? It's under the Applications menu, ma'am. That's in the top-left corner, ma'am. No, that's the clock. Other side. No, ma'am, I meant go left, not go down. I'm sorry ma'am..." :D

---

### Post by tuatha1337 on 2007-05-12
```
linux@Linux-desktop:~$ cat /etc/apt/sources.lst
cat: /etc/apt/sources.lst: No such file or directory
```
No worries about this "overwhelming" stuff. It's actually easy to understand once I actually get to using it. I just wish I knew what all this stuff meant. There is a place that has information on all of this right?

---

### Post by Happy_Man on 2007-05-12
Whoops, forgot an i.
```
cat /etc/apt/sources.list
```

---

### Post by tuatha1337 on 2007-05-12
Hope you're ready for this one.

```
linux@Linux-desktop:~$ cat /etc/apt/sources.list

deb http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by jfinkels on 2007-05-12
> **tuatha1337 said:**
> ```
linux@Linux-desktop:~$ cat /etc/apt/sources.lst
cat: /etc/apt/sources.lst: No such file or directory
```
No worries about this "overwhelming" stuff. It's actually easy to understand once I actually get to using it. I just wish I knew what all this stuff meant. There is a place that has information on all of this right?

Use Google and poke around for some information on "Linux terminal howto" or something like that. If you want info on a command, type 'man' and then the name of the program/command, like this:
```
man cat
```
It's one of the greatest things about Unix-like operating systems.

Did you install azureus using a downloaded file from azureus' website? Stick with either the graphical package manager, Synaptic, or the command line equivalent on which Synaptic is based, 'aptitude' (or 'apt-get', but I prefer aptitude, see here for more info on that [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)). For more info on installing programs, take a look here: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

To enable the universe repository, which has MANY applications available for you to install very easily with Synaptic, go to "System > Administration > Software Sources" and check the box next to 'universe'. Happy_Man might tell you a different way of accomplishing the same thing (it's easier for us to give you commands to type than it is for us to write out long directions like this).

Then type the following command to install azureus (or any program in the repositories):
```
sudo aptitude install azureus
```

To find out what the launcher on your desktop links to, right click it, select "Properties..." go to the last tab, which says "Launcher" and see the section called "Command:". That's what the launcher executes when you double click it!

---

### Post by Happy_Man on 2007-05-12
Yep, where you see
> # deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
make them
> deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

EDIT: jfinkels, Feisty has been out for what, a month? And here you are already testing GUTSY? What gives?

---

### Post by jfinkels on 2007-05-12
> **Happy_Man said:**
> Yep, where you see

make them


EDIT: jfinkels, Feisty has been out for what, a month? And here you are already testing GUTSY? What gives?
I must admit...I have a problem...

I have an obsession with updating packages. :D

Actually, I was using Gutsy before, but not anymore. I should change that so I don't seem like a pompous *burro*.

---

### Post by AntonGardner on 2007-05-15
Try to give the command:
```
java --version
```
or
```
java -version
```

If the version is 1.4.2, you have to uninstall the **libgcj-common** package and install the **sun-java6-jre** package. Your azureus will work fine. :popcorn:

---

### Post by tuatha1337 on 2007-05-16
Yup, it's 1.4.2. Uninstalling libgcj-common with synaptic removes azureus as well. How do I get around this?

---

### Post by Happy_Man on 2007-05-17
You can't, since Azureus needs Java to run. Sorry...

---

### Post by AntonGardner on 2007-05-28
Now you have to install the package: sun-java6-jre and its dependencies. Then go to [http://azureus.sf.net](http://azureus.sf.net), download the new version of azureus for Linux and start it!

---

