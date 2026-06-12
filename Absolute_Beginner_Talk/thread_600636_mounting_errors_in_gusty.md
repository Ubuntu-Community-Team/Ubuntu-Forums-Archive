---
title: "mounting errors in gusty"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by pienose on 2007-11-02
I have just upgraded to gusty, and it is working fine. Except for one big problem, I cannot mount anything (like my mp3 player). When I login, I get the error-

```

Hall error

cannot initialize hal 
```

or something similar.
Then when I connect my sandisk sansa e200 in msc mode the player tells me it is disconnected and nothing happens on the PC. When I go to system->preferences-> removable drives and media I get the error-

```
Volume management not supported

The "hald" service is required but not currently running. Enable the service and rerun this application, or contact your system administrator.

Note: You need Linux kernel 2.6 for volume management to work.
```

please somebodey help.

Thanks!

---

### Post by Pumalite on 2007-11-02
[http://www.penguin-soft.com/penguin/man/8/hald.html](http://www.penguin-soft.com/penguin/man/8/hald.html)
[http://lists.freedesktop.org/archives/hal-commit/2004-November/000749.html](http://lists.freedesktop.org/archives/hal-commit/2004-November/000749.html)
[http://gentoo-wiki.com/HOWTO_D-BUS,_HAL,_KDE_media:/](http://gentoo-wiki.com/HOWTO_D-BUS,_HAL,_KDE_media:/)
I hope they help.

---

### Post by pienose on 2007-11-02
sorry, but no I now understand a bit more about what they are but I cannot find a solution to my problem.

---

### Post by Pumalite on 2007-11-02
I've been looking for it, but can't find it either.

---

### Post by Centx on 2007-11-02
Could you please post the output of the command "ps aux | grep hald" here?

---

### Post by pienose on 2007-11-02
shure, here ya go-

tim@ubuntu:~$ ps aux | grep hald
tim       6604  0.0  0.1   2972   748 pts/0    D+   20:44   0:00 grep hald

---

### Post by Centx on 2007-11-02
So what have you tried this far?
Have you tried to search for hald with aptitude, although It should be installed by default, and installed it if it wasn't installed? or does this seem like a bug of some sort?
Can you start it with ```
sudo /etc/init.d/hal start
```? and what output do you get if started this way?

---

### Post by pienose on 2007-11-02
To be honest I have no I dea what you are talking about!
that is why I posted this in the beginers forum, I have know idea how mounting works, or what this hall thing is. when I run that I get the responce-

tim@ubuntu:~$ sudo /etc/init.d/hal start
[sudo] password for tim:
 * Starting Hardware abstraction layer hald                  
 tim@ubuntu:~$

---

### Post by Centx on 2007-11-02
> **pienose said:**
> To be honest I have no I dea what you are talking about!
that is why I posted this in the beginers forum, I have know idea how mounting works, or what this hall thing is. when I run that I get the responce-

tim@ubuntu:~$ sudo /etc/init.d/hal start
[sudo] password for tim:
 * Starting Hardware abstraction layer hald                  
 tim@ubuntu:~$

hald is the daemon (think background process from windows) that for example tells applications that a device has been plugged into the computer (thats a very easy way to say it).
Its an acronym for Hardware Abstraction Layer, and before this you mostly had to "mount" devices yourself... now after you've started this daemon, does the USB device work for you?

---

### Post by pienose on 2007-11-03
no, it has the same result as before. Thanks for clearing that up for me, I did know some of that but not what a daemon was, thanks!

---

### Post by Centx on 2007-11-03
> **pienose said:**
> no, it has the same result as before. Thanks for clearing that up for me, I did know some of that but not what a daemon was, thanks!
No problem =)
But does this mean that the output of "ps aux| grep hald" yields the same output after you've started hald with "/etc/init.d/hal start"? That would mean that hald actually isn't started, or starts and crashes right afterwards which either could be caused by a bug in Ubuntu, or some custom modification.

---

### Post by pienose on 2007-11-03
sorry, I didn't quite get that here is the out put of "ps aux| grep hald"-

tim@ubuntu:~$ ps aux| grep hald
tim      11461  0.0  0.1   2988   748 pts/0    D+   23:30   0:00 grep hald

and "/etc/init.d/hal start"

tim@ubuntu:~$ /etc/init.d/hal start
open: Permission denied
 * Can't start Hardware abstraction layer - detected chrooted session

chrooted session? wtf?

---

### Post by Centx on 2007-11-03
> **pienose said:**
> sorry, I didn't quite get that here is the out put of "ps aux| grep hald"-

tim@ubuntu:~$ ps aux| grep hald
tim      11461  0.0  0.1   2988   748 pts/0    D+   23:30   0:00 grep hald

and "/etc/init.d/hal start"

tim@ubuntu:~$ /etc/init.d/hal start
open: Permission denied
 * Can't start Hardware abstraction layer - detected chrooted session

chrooted session? wtf?

sorry bout' that, was of course to be ```
 % sudo /etc/init.d/hal start
```
and ```
%ps aux|grep hald
```

The output of the ps command shows what processes are currently running, and grep hald shows only those that contains the string "hald" which all is there to show if hald is up and running after a manual start. If it isn't, you've got to debug some =/

---

### Post by pienose on 2007-11-04
tim@ubuntu:~$ % sudo /etc/init.d/hal start
bash: fg: %: no such job

tim@ubuntu:~$ %ps aux|grep hald
bash: %ps: command not found

hm, I command not found? no such job, does that mean there is no processes running with 'hald' in them?

---

### Post by pienose on 2007-11-04
Hello? anybody? I really need to get this to work!!

---

### Post by Centx on 2007-11-05
> **pienose said:**
> tim@ubuntu:~$ % sudo /etc/init.d/hal start
bash: fg: %: no such job

tim@ubuntu:~$ %ps aux|grep hald
bash: %ps: command not found

hm, I command not found? no such job, does that mean there is no processes running with 'hald' in them?

I'm really sorry for this, I kinda take it for granted that someone is used to the CLI, as I myself use it quite a bit =)

You see, when i write ```
% sudo /etc/init.d/hal start
``` I mean that you should execute  the command "sudo /etc/init.d/hal start" in some sort of shell :), I forgot that the "%" is used to 
bring back background jobs!

Just execute those commands, without the "%" and post the output again. 

Here's mine, more power to the examples! : ```
centx@xeon:~% sudo /etc/init.d/hal start
[sudo] password for user:
 * Starting Hardware abstraction layer hald                                     /usr/sbin/hald already running.
                                                                         [ OK ]
centx@xeon:~% 

```
As you can read, my hald-daemon is running, and everything is quite ok =)

and for ps: ```
centx@xeon:~% ps aux|grep hal
108       4917  0.0  0.2   5524  3736 ?        Ss   18:00   0:00 /usr/sbin/hald
root      4918  0.0  0.0   3092  1020 ?        S    18:00   0:00 hald-runner
108       4979  0.0  0.0   2160   896 ?        S    18:00   0:00 hald-addon-keyboard: listening on /dev/input/event2
108       4980  0.0  0.0   2164   896 ?        S    18:00   0:00 hald-addon-keyboard: listening on /dev/input/event4
108       4981  0.0  0.0   2164   896 ?        S    18:00   0:00 hald-addon-keyboard: listening on /dev/input/event5
108       4984  0.0  0.0   2164   884 ?        S    18:00   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
108       5026  0.0  0.0   3260  1188 ?        S    18:00   0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
centx     7466  0.0  0.0   2976   768 pts/2    S+   18:26   0:00 grep hal
centx@xeon:~% 

```

---

### Post by pienose on 2007-11-05
don't worry, I got it to work. Not quite shure how but I did!

---

### Post by Centx on 2007-11-05
> **pienose said:**
> don't worry, I got it to work. Not quite shure how but I did!

So now it works upon reboots too? Grats, and lets hope its stays that way :)

---

### Post by pienose on 2007-11-07
well actually...I had to do a fresh install and now it's back!! 

I think I know what command it was that fixed it, it had someing to do with two files on ending in 2 and the other in 3 and then swapping them over or parts of them...Argh!!
I have done a lot of serches invloving hal and that lot. but noting.

---

