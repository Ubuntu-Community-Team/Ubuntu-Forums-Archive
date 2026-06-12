---
title: "enabling extra repositories"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Morkhaar on 2007-05-12
hi,
to cut a loooong way short, I messed up my nvidia drivers and cannot access a graphic environment. 
I already tried ** dpkg-reconfigure xserver-xorg** but it doesn't work...
I'm trying to install ENVY but in order to do so I have to enable the extra repositories (including universe and multiverse) only through a terminal. Searching a bit, it seems that I have to copy paste a significant amount of lines to a file, that I simply cannot do any other way but writing it down.
is there a simple set of commands to be able to do it flawlessly? 
any howto link would be greatly appreciated. I already found one but as mentioned above the writer reasonably assumes you CAN actually copy paste what he says...

in any way, thanks to all in this forum for their support so far

---

### Post by jtraub on 2007-05-12
What lines and where from you would like to copy-paste? Theare a lot of methods depending source and target.

---

### Post by Morkhaar on 2007-05-12
well so far, I've only come up with this: [http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")
check it out, to me it seems I cannot do it just like it says

ok, i could write it down it's not thaaaat big, I'm just trying to spare my self some time and frustration from probable mistakes in the procedure...

---

### Post by AAM on 2007-05-12
You need to get to a command line and type:
> sudo nano /etc/apt/sources.list
a text editor will open with this file open, go to the bottom and type in your extra lines, then follow the commands (write OUT, select FILE_NAME given and EXIT). Go back to the commandline and type something else which will look like:
> sudo apt-get update, or
sudo apt-get remove nvidia-glx, and later
sudo apt-get install nvidia-glx
Now I can't guarantee that this will work because I have misunderstood your problem, but it's a good place to start.

---

### Post by AAM on 2007-05-12
sorry duplicate

---

### Post by jtraub on 2007-05-12
Hm... Try in console 
```
wget http://www.psychocats.net/ubuntu/sources
```
After that open it in your favorite console editor and delete all unneeded lines and htmk tags

---

### Post by jtraub on 2007-05-12
I think that your sources.list already contains all lines what you need, you should just uncomment them

---

### Post by Morkhaar on 2007-05-12
thanks for the tips!
my problem is a bit more complicated than that AAM...
anyway I ll try and find out if any of this works

---

