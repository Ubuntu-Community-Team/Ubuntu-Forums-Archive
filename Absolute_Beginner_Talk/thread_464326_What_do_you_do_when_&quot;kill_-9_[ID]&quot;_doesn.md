---
title: "What do you do when &quot;kill -9 [ID]&quot; doesn't work?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-06-04
I had a <defunct> process so I killed it (kill [ID]); that didn't work, so I sigkilled it (kill -9 [ID]); but that didn't work either. what option is left?

---

### Post by Nekiruhs on 2007-06-04
```
kilall -9 processID
```
Did you get the process ID right?

---

### Post by arijarot on 2007-06-04
> **Nekiruhs said:**
> ```
kilall -9 processID
```
Did you get the process ID right?

I tried that and it told me :
 ```
killall -9 5453 
5453: no process killed

```

this is the right process (netstat), I've triple checked....

---

### Post by arijarot on 2007-06-04
I've also restarted my pc three times and netstat goes zombie / <defunct> every time and won't listen to "kill" , "killall"...

---

### Post by cytutchi on 2007-06-04
I can suggest some ideas but don't know if it the correct answers but have a look

maybe try :

sudo kill -9 <proccessid>

maybe root will do the job
btw why do you use killall and not just kill?
but you know what...? if the process is essential maybe indeed it canot be killed until you restart your pc ???

---

### Post by arijarot on 2007-06-04
> **cytutchi said:**
> I can suggest some ideas but don't know if it the correct answers but have a look

maybe try :

sudo kill -9 <proccessid>

maybe root will do the job
btw why do you use killall and not just kill?
but you know what...? if the process is essential maybe indeed it canot be killed until you restart your pc ???

I've tried sudo for all variations, see above. I also restarted three times and each time the process (netstat) goes <defunct>, as it is right now...

---

### Post by Nekiruhs on 2007-06-04
5453 is not the PID its probably netstat. As far as I know typing killall -9 firefox-bin kills firefox, so killall -9 gnome-terminal from another terminal might work.

---

### Post by arijarot on 2007-06-04
> **Nekiruhs said:**
> 5453 is not the PID its probably netstat. As far as I know typing killall -9 firefox-bin kills firefox, so killall -9 gnome-terminal from another terminal might work.

hmm... the PID changes each time, now it's 5122, for instance. unfortunately, the suggestion to kill the terminal didn't work either. it's curious, because it's a user level process and not root, which btw, I didn't start...

```


ps -ux | grep netstat

USER         PID   %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
arijarot     5122  0.0  0.0      0     0 ?        Z    16:10   0:00 [netstat] <defunct>



```

---

### Post by Cypher on 2007-06-04
If a process goes <defunct> and then ZOMBIE, it cannot be killed or removed. The only way of getting rid of it is to reboot the machine. A [Zombie process]("http://en.wikipedia.org/wiki/Zombie_process") is essentially one that has finished it's work but it's parent basically abandoned it and thus has lost the link to control/kill/modify it.

Also, the PID should indeed change each time you re-start the machine, only in a very controlled systems will the system have the same PID for the processes that start up.

If you aren't starting the process yourself, perhaps it's something in the boot-up scripts you can modify??

---

### Post by arijarot on 2007-06-04
> **Cypher said:**
> If a process goes <defunct> and then ZOMBIE, it cannot be killed or removed. The only way of getting rid of it is to reboot the machine. A [Zombie process]("http://en.wikipedia.org/wiki/Zombie_process") is essentially one that has finished it's work but it's parent basically abandoned it and thus has lost the link to control/kill/modify it. 
OK, makes sense...but why would this happen each time I reboot?

> Also, the PID should indeed change each time you re-start the machine, only in a very controlled systems will the system have the same PID for the processes that start up.

> If you aren't starting the process yourself, perhaps it's something in the boot-up scripts you can modify?? good suggestion :-k, any idea how ? ;-)

---

### Post by Cypher on 2007-06-04
For starters, in a terminal do the following
```

cd /etc/init.d
cat * | grep netstat

```
If you get some file showing, perhaps we can look at that file and figure out why 'netstat' is being started..

---

### Post by Nekiruhs on 2007-06-04
Preferences > Session, Look for the process on all tabs, and go from there (Sorry if im wrong, I used to use GNOME, now I'm using KDE)

---

### Post by arijarot on 2007-06-04
> **Cypher said:**
> For starters, in a terminal do the following
```

cd /etc/init.d
cat * | grep netstat

```
If you get some file showing, perhaps we can look at that file and figure out why 'netstat' is being started..

Good idea! I got the same one after reading the [zombie process]("http://en.wikipedia.org/wiki/Zombie_process") link that you posted. I followed it up to it's parent (firefox-bin) and killed the parent (lol), which killed the zombie child \\:D/ Thanks, Cypher!

edit: now I just need to figure out why every time firefox runs, it spawns zombie netstat child processes?!

---

### Post by Cypher on 2007-06-04
Ahh..so it's firefox that is spawning netstat..I wonder why..but glad we got it figured out at least..:)

---

### Post by Nekiruhs on 2007-06-04
> **arijarot said:**
> Good idea! I got the same one after reading the [zombie process]("http://en.wikipedia.org/wiki/Zombie_process") link that you posted. I followed it up to it's parent (firefox-bin) and killed the parent (lol), which killed the zombie child \\:D/ Thanks, Cypher!
I'm sorry, but can I make a movie of that? Its a pretty epic script, killing a Zombie parent to end a zombie childs life! Ooh, I get shudders just thinking about it! LOL!

---

### Post by arijarot on 2007-06-04
> **Nekiruhs said:**
> I'm sorry, but can I make a movie of that? Its a pretty epic script, killing a Zombie parent to end a zombie childs life! Ooh, I get shudders just thinking about it! LOL!

lol you should see the link [http://en.wikipedia.org/wiki/Zombie_process](http://en.wikipedia.org/wiki/Zombie_process), there are also orphans !

---

### Post by arijarot on 2007-06-04
> **Cypher said:**
> Ahh..so it's firefox that is spawning netstat..I wonder why..but glad we got it figured out at least..:)

I'm rather curious about that too...hmmm:-k

---

