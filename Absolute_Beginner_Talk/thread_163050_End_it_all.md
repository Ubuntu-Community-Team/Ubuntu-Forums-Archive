---
title: "End it all"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-20
I have used a program called Enditall, on Windows. 
[http://www.the-old-sea-dog.net/enditall.html](http://www.the-old-sea-dog.net/enditall.html)

What it does is, closes all running processors, that is not required to run windows. 

Is there anything simulair to Ubuntu?

---

### Post by Charax on 2006-04-20
To close your running *processors*? I should hope not, otherwise your PC will stop working. however, there is a command to terminate all nonessential *processes*, I think it's the Killall command

---

### Post by aktiwers on 2006-04-20
Yes, thats what i ment. Sorry for my typo :)

Could you give me the command I need to do this?

```
killall
```

Is that all? Nothing seems to happend when I do this.

EDIT:

Or yes this happends:

```
aktiwers@ubuntu:~$ killall
usage: killall [ OPTIONS ] [ -- ] name ...
       killall -l, --list
       killall -V --version

  -e,--exact          require exact match for very long names
  -I,--ignore-case    case insensitive process name match
  -g,--process-group  kill process group instead of process
  -i,--interactive    ask for confirmation before killing
  -l,--list           list all known signal names
  -q,--quiet          don't print complaints
  -s,--signal         send signal instead of SIGTERM
  -v,--verbose        report if the signal was successfully sent
  -V,--version        display version information
  -w,--wait           wait for processes to die

```

---

### Post by Charax on 2006-04-20
Think so. Type man killall to get all the instructions.

killall -l will list all the running signals (processes) by name, then you can killall [*signalname]* for each of them if you can't get killall to do it.

---

### Post by Gustav on 2006-04-20
The difficulty is in knowing which processes that are vital for the system to run.

---

### Post by aktiwers on 2006-04-20
[QUOTE=Gustav]The difficulty is in knowing which processes that are vital for the system to run.[/QUOTE]

Yes, exactly!
I would still like to be able to run my system bugfree and with access to the internet. Actually I used that program a lot in Windows, because its an easy way to close down everything fast, without closing the or restarting the whole system. 

The closest I have come to do this is to do a CTRL+ALT+BACKSPACE, but then I have to log on again, and programs that starts when I turn the PC on, also starts again.

---

