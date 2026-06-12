---
title: "core dumped - epiphany"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by beanco on 2008-01-16
I had some wierd problems with my braowers, all three - EPiphany, Galeon, Firefox


They kept closing, I rebooted and tried using them again, then they did it again.

So, I tried to run Epiphany from terminal and got the core dumped mssage as soon as I tried to browse in Epiphany.

So, any ideas?

Robi

---

### Post by Cypher on 2008-01-16
What version of Ubuntu are you using? Are you up-to-date on the latest updates?

---

### Post by beanco on 2008-01-16
on feisty and I have not updated recently...

robi

ps, easiest way to update from cl = sudo apt-get update or sg like that?

---

### Post by Cypher on 2008-01-16
Yeah.."sudo apt-get update ephiphany" should check to see if there is an update and install it..

---

### Post by Joeb454 on 2008-01-16
I had this problem with Firefox 2 yesterday.

And I'm running Gutsy with all updates and therefore the latest Firefox

---

### Post by beanco on 2008-01-16
> **Cypher said:**
> Yeah.."sudo apt-get update ephiphany" should check to see if there is an update and install it..


rob@rob-desktop:~$ sudo apt-get update ephiphany
E: The update command takes no arguments




 what that mean?

---

### Post by Cypher on 2008-01-16
Actually..sorry.."update" will update the system..you want to use "install" instead..even it's installed, it will update or tell you you have the latest version..

---

### Post by beanco on 2008-01-16
got this...


```
rob@rob-desktop:~$ sudo apt-get install  ephiphanyReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ephiphany
rob@rob-desktop:~$ 

```

robi

---

### Post by Cypher on 2008-01-16
The package is called "epiphany-browser". You can get the package name by doing
```

dpkg -l | grep ephiphany

```

---

### Post by beanco on 2008-01-16
and now this


```
rob@rob-desktop:~$ sudo apt-get install ephiphany-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ephiphany-browser
rob@rob-desktop:~$ 

```

---

