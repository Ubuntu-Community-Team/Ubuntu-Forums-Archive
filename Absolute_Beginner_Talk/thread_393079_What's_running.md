---
title: "What's running?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Trebuchet on 2007-03-25
How can I tell what apps are currently running in Ubuntu, and close any I don't want running? I think I must have at least a dozen instances of Firefox running at the moment because when I minimize it it vanishes completely and I have to reopen it.

---

### Post by Bachstelze on 2007-03-25
*ps ax* to see all the running processes and *ps e* to just see the ones started by you.

---

### Post by raul_ on 2007-03-25
```
top
```  then "k" for Kill, signal number 9, and the PID (process ID) of the app you want to close.

OR

use the command posted above and then

```

kill -9 <PID>

```

---

### Post by Trebuchet on 2007-03-25
> **HymnToLife said:**
> *ps ax* to see all the running processes and *ps e* to just see the ones started by you.That's just Sanskrit to me. Ps ax and ps e where? In the terminal?

---

### Post by Trebuchet on 2007-03-25
I still need help here. I have no idea what apps are running. 

Would somebody please reply in language a noob would understand?

---

### Post by hyper_ch on 2007-03-25
Open a terminal and enter the commands posted above...

```

top

```
--> In order to leave "top" you just press "q"


```

ps ax

```

```

ps e

```

```

ps aux

```

---

### Post by Trebuchet on 2007-03-25
OK. That's not much help because I don't know what many of these terms mean, but I can't see any sign my firewall (Firestarter) is running. The terminal shows 94 total, 1 running, 92 sleeping, 1 zombie. Zombie doesn't sound good.

Why aren't running apps shown on the toolbar? Why doesn't Firestarter even show on my Applications menu? EDIT: Found it in the System/Administration menu.

Sorry I sound so dumb here. :(

---

### Post by kostkon on 2007-03-25
Hi Trebuchet,

yes a simple way to see what is running is to go to the* System Tools* menu and run the *System Monitor* application. You will be able to see what processes are run by you and kill any process you like.

Now to solve your problem of not seeing your apps on your toolbar (called a panel in linux) just right click on the panel, select *Add to Panel* and from the list of the applest you will available for adding, select the * Window List* applet.

---

