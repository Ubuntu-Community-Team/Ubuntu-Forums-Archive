---
title: "big problem with terminal"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by FireStorm102389 on 2007-08-09
ok, i was trying to install java with it...well, it went into a blue background with a grey box eplaining the terms of agreement or something, and i couldn't click ok, and didn't know how...so I restarted my comp...now i try to make updates in adept manager and I can't do ANYTHING cuz it says that it is still running but idk how to stop it cuz the terminal with it in it isn't up anymore and idk how to stop it.

PLEASE SOME1 HELP

---

### Post by FireStorm102389 on 2007-08-09
does anyone know how to fix this problem?

---

### Post by mcduck on 2007-08-10
It's a terminal, you can't click things with mouse there :) Insteasd just use tab or arrow keys to move the focus to the OK button and then click Enter.

Anyway, to fix the problem afterwards try running 'sudo apt-get update" in a terminal and post here the error it gives you.

---

### Post by DeHorde on 2007-08-10
Go to: System > Adminitration > system monitor and click on the tab [processes]. 
Look for processes called either apt-get or dpkg. Kill them (right click > kill process).

Now you have an apt-get which does not know which side is up. Now do a ```
sudo apt-get update 
``` in a terminal like mcduck said. It will tell you it's got problems, and most probably tell you what to do next: My bet is on ```
sudo apt-get -f install
```. 

PS: If you have not gotten scared of the command line yet: ```
ps
``` or ```
pstree
``` in a terminal is your friend here. also look into ```
kill
``` and ```
pgrep
```.

---

### Post by bluemarvel on 2007-08-10
> **DeHorde said:**
> Go to: System > Adminitration > system monitor and click on the tab [processes]. 
Look for processes called either apt-get or dpkg. Kill them (right click > kill process).

Now you have an apt-get which does not know which side is up. Now do a ```
sudo apt-get update 
``` in a terminal like mcduck said. It will tell you it's got problems, and most probably tell you what to do next: My bet is on ```
sudo apt-get -f install
```. 

PS: If you have not gotten scared of the command line yet: ```
ps
``` or ```
pstree
``` in a terminal is your friend here. also look into ```
kill
``` and ```
pgrep
```.

One thing that I do in terminal A LOT is kill Firefox because of that YouTube/Flash bug that occasionally causes Firefox to lock up on a few computers.

```

$ ps aux | grep firefox

```

The top line will show what processes called "Firefox" are running. It looks like this:

```

acctname 11524  1.3  3.3 174300 68764 ?        Sl   09:17   1:42 /usr/lib/firefox/firefox-bin 
acctname 15153  0.0  0.0   2884   760 pts/0    S+   11:28   0:00 grep firefox

```

The first entry shows Firefox is running under process 11524, the second shows that my 'grep' command is running under 15153.  So you just do this:

```

$ kill 11524

```

That will kill the Firefox process completely and you can just start it up again. This is just an example of how you can do this with any process or program that you have running.

---

### Post by Nythain on 2007-08-10
sudo atitude clean
sudo aptitude update
might do the trick

---

