---
title: "How to learn the tricks of Ubuntu"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-09-22
I'm pretty happy right now because I got my Ubuntu up and running with all the functionality I can think of right now (thanks to automatix). However, I'm interested in getting to learn the system as well as I know XP (which is very well). Obviously, the obvious answer for this is to just keep using the system and check forums, but what would be a good way to augment that so I can learn this stuff faster? A lot of what I'm interested in is how the filing hierarchy is set up and I'd like to learn the more commonly used terminal commands. Thanks.

---

### Post by hearnden on 2006-09-22
Best way to learn is to have a goal that requires learning.  One of the best tools for learning commands is to read the man pages, which often give examples and suggest other commands.  However the problem with that is that you need to know the commands first!  I'd been using Unix and Linux for 6-7 years before I discovered the 'file' command, and it is so useful!

For navigating around the file hierarchy here are some commands that, once you start learning about them, should help you to be more productive as well as understand more about what's going on. (I've left off the really really obvious ones, ls, mkdir, ...)

Finding:
```

$ locate
$ updatedb
$ find

```

Manipulating:
```

$ ln
$ mount
$ mknod

```

Managing:
```

$ chmod
$ chown
$ chgrp
$ file

```

---

### Post by nudnik on 2006-09-22
There is an Ubuntu book available on the Ubuntu homepage which covers details regarding Dapper Drake.

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

See the website above for learning the terminal commands right away.

---

### Post by hearnden on 2006-09-22
Oh and of course, to get started with general terminal usage:

```

$ man man
$ man bash

```

---

### Post by orb9220 on 2006-09-22
[http://www.unix-tutorials.com/tutorials.php?os=Ubuntu](http://www.unix-tutorials.com/tutorials.php?os=Ubuntu)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by mongooseman1128 on 2006-09-22
Oh sweet guys (or girls) I tried those three links. That first one is awesome for terminal and the other two are pretty sweet too. Thanks also hearnden those command examples are very much appreciated I'm starting to kind of play around in terminal. (hope I don't screw anything up) Thank you so much everyone you've been awesome.

---

### Post by DarkPCTroll on 2006-09-22
Hello...

Here you have If you're hungry.. those links above are really good though, but then again... if you're hungry here you have, it has helped me a lot.

[http://linux.org.mt/article/terminal]("http://linux.org.mt/article/terminal")

I hope it'll be helpful to someone. 

Regards

**_Dark PC Troll_**

---

### Post by Brunellus on 2006-09-22
Also buy a book that's good and not distribution-specific.  My handy-dandy reference is "How Linux Works" by Brian Ward (No Starch Press).  Command-line centric, but very very very useful.

---

### Post by skymt on 2006-09-22
Another good link: [Rute User's Tutorial and Exposition](http://rute.2038bug.com/rute.html.gz). Stupid name, awesome book. Some of it is slightly dated, but the command-line stuff never changes.

---

### Post by Dinerty on 2006-09-22
Eveyone learns different, some by listening/reading amongst other things. If you really want to learn then dive in, don't just keep to one aspect/area of Ubuntu, for instance instead of downloading .deb try and download source code and compile yourself.

I learnt a lot about source code this way and find it more intresting to install this way.

Learn about terminal commands instead of using gui for everything, you may think its a quicker to use gui to , however if you need to copy folders from your desktop to say /home/bob/.icons instead of having to highlight all the folders you wanted to copy, then right click and say copy, then load Nautilus, and go search for the particular folder, then right click and paste the files in, you could simply

```
cp -r /home/dinerty/Desktop/t2 /home/dinerty/Desktop/t1 /home/dinerty/.icons 
```

You can also drag the folder/file you want onto the terminal and it will paste the path for you

Check this [http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)

---

