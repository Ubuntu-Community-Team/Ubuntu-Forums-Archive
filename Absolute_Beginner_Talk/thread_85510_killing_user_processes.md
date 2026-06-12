---
title: "killing user processes"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by ctcecil on 2005-11-02
I vaquely remimber when administering a game server using linux i could use
$ who
to find out users logged in and there was something i could do to see all the processes they were running and $ kill them...

can you kill programs instead of killing the whole user or am i dreaming?

---

### Post by Manny C on 2005-11-02
Yes. On ordinary systems (ie. not game servers), you can kill processes by issuing the ```
 kill [pid] 
``` command.

So if for example, if firefox is hung, and I want to kill the firefox process i do the following:
```

manny@kubuntulap:~$ ps aux | grep firefox
manny  17863  3.9  7.6 123692 56520 ?        Sl   12:09   0:55 /usr/lib/mozilla-firefox/firefox-bin -a firefox
manny  18033  0.0  0.0   2936   628 ttyp1    R+   12:32   0:00 grep firefox

``` to find what the PID (process ID number) is, and then issue the following to kill the firefox process:
```
 kill 17863 
``` If this doesn't work, then the following will definitely work (indiscriminantly kills without prejudice or fear!):
```
 kill -9 17863 
``` Another way is to use the killall command. In this case I don't need the PID. I just use the program name:
```
 killall firefox 
``` 
If a program is being run by root, then you need to prefix all of the above (excluding the ps aux command) with sudo.

Hope this helps.

---

### Post by Joe_lurker on 2005-11-02
You can run the command 'ps aux' to see all of the running processes.  Read the man page a complete list of options, it's quite extensive.

To kill a process find it with 'ps'.  Use the command 'kill -9 <PID>' where <PID> is the process ID of the process.

To find a particular users process use 'ps -U <username>' replacing <username> with the name of the user.

-Joe

---

### Post by xequence on 2005-11-02
I have no idea about those "kill 17863" things, but if something messes up I do "killall" then the name of what it is. For example, "killall perlpanel".

---

### Post by wylfing on 2005-11-02
For something that fairly closely mimics what Windows admins get when they hit Ctrl-Alt-Del, choose Applications > System Tools > System Monitor from the main menu. You can select running processes and kill them.

---

### Post by Donnut on 2005-11-02
I just have a forcequit Icon on one of my panels.  It works...

---

