---
title: "Some basic shell questions"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Limitlesschannels on 2007-04-16
So, I have been going through linuxcommand.org to start learning my stuff on the command line side of linux and I have just been looking at piping and I/O redirection.  Pretty basic, but I was just trying to figure out a simple way of enabling commandline execution with output to a specified file in the same command; i.e. when i run uTorrent through WINE:
MyName@MyComputer:~$ wine utorrent.exe
    but if i want to get the terminal output to a text file in my working directory [ so if I happened to have an error I could post it rather easily], how would I go about that?
```

MyName@MyComputer:~$ wine utorrent.exe > utorrent_launch.txt

```

creates the file, but does not send output to created file.

```

MyName@MyComputer:~$ wine utorrent.exe | > utorrent_launch.txt

```

I would not expect this to really work anyway, but it was worth a shot.  It gave me the same results as the first.

So, any basic-elements/basic-understandings/commands/ideas that i am not getting?

---

### Post by Jussi Kukkonen on 2007-04-16
Often something like this happens because there are actually two different output streams (standard error and standard output). Try this:
```
wine utorrent.exe >utorrent_launch.txt 2>&1
```
The last part means "send stderr to same file as stdout".

---

