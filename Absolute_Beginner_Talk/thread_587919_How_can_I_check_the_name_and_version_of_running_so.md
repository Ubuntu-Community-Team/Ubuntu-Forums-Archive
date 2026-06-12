---
title: "How can I check the name and version of running software?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-10-23
One of the problems I have is that I fiddle away and suddenly something works. I have no idea why.
 
Is there a way of getting a definitive list of software (name and version) that is running so that I can check what is going on. 

I am particularly interested in how my BBC News streaming works. It has been a real pain in the past and peeps still post with problems. I would like to help them out but don't know exactly what is needed even though my system runs perfectly as far as I can tell.

Thanks, Bob

---

### Post by drs305 on 2007-10-23
System Monitor (System, Administration, System Monitor) shows what processes are active and a right click on a process can show what files it opened.

To simply see what processes are running, you can type:
```
ps -u <username> 
``` 
The ps command has many options which you can view by typing:
```
ps --man 
``` 

There have to be better options than these 2 so hopefully someone will respond.

Synaptic shows the installed version and latest version numbers.

---

### Post by CowzRule on 2007-10-23
Synaptic Package Manager will show you all the installed software and what version it is and you can usually click on Help - About to get the version of software also.

---

### Post by bwallum on 2007-10-23
> **drs305 said:**
> System Monitor (System, Administration, System Monitor) shows what processes are active and a right click on a process can show what files it opened.

To simply see what processes are running, you can type:
```
ps -u <username> 
``` 
The ps command has many options which you can view by typing:
```
ps --man 
``` 

There have to be better options than these 2 so hopefully someone will respond.

Synaptic shows the installed version and latest version numbers.

Thanks, works a treat. I also found System>Administration>System Monitor then the process tab shows the same thing. It is amazing how much simpler the command line is over GUI. I really must try to learn more commands.

Thanks again
Bob

---

### Post by bwallum on 2007-10-23
Thanks cowz, drs has some added stuff that was on the button too.

---

### Post by staticsage on 2007-10-23
> **bwallum said:**
> Thanks, works a treat. I also found System>Administration>System Monitor then the process tab shows the same thing. It is amazing how much simpler the command line is over GUI. I really must try to learn more commands.

Thanks again
Bob

You can also get that much detail using ps.

If you type ps -A it will list all processes just as you see it in the System Monitor GUI.

---

