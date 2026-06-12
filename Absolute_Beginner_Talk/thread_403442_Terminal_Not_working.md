---
title: "Terminal Not working?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by sentics on 2007-04-07
Hello all.  

I have a problem.  Every time I type a command into the terminal I always get "command not found"(yes Ive checked and they should work).   Anyone know what I'm doing wrong.  And just to warn you I'm a complete noob at Linux.   :)

---

### Post by 23meg on 2007-04-07
Can you name some commands as examples? What do you get when you type ```
df -h 
```for example?

---

### Post by sentics on 2007-04-07
Now that I got something however this for example I did not.
I was setting up a tv output;

kyler@kyler-laptop:~$ sudo gedit /usr/bin/switchmon
Password:
kyler@kyler-laptop:~$ sudo chmod +x /usr/bin/switchmon
kyler@kyler-laptop:~$ sudo chmod +x /usr/bin/switchmon
kyler@kyler-laptop:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.single
kyler@kyler-laptop:~$ sudo /etc/X11/xorg.conf.svideo
sudo: /etc/X11/xorg.conf.svideo: command not found
kyler@kyler-laptop:~$ sudo chmod +x /usr/bin/switchmon


If youd like to see the instructions there located here:  [http://ubuntuforums.org/showthread.php?t=361124&highlight=dual+screen](http://ubuntuforums.org/showthread.php?t=361124&highlight=dual+screen)

Thanks for the fast reply!

---

### Post by 23meg on 2007-04-07
First of all, for graphical applications such as Gedit, it's a good practice to use *gksudo* instead of *sudo*, so substitute all instances of *sudo* with *gksudo* in those instructions. 

The line "sudo /etc/X11/xorg.conf.svideo" is erroneous; since you're looking to edit the file, it should be ```
gksudo **gedit **/etc/X11/xorg.conf.svideo
```

See the following for more information on *sudo*/*gksudo*:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sentics on 2007-04-07
Okay seems to have worked up to the point of the Launcher created to manage these.   When I type in the appropriate number I get again command not found.  Any Ideas?   Also thanks alot for the help!

---

### Post by 23meg on 2007-04-07
Please copy and paste your input, and the exact error you get.

---

### Post by sentics on 2007-04-07
I seem to have got it working.  Thank you very much for your help. ^.^

---

