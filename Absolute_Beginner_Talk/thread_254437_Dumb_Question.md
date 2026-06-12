---
title: "Dumb Question?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by dolphinsonar on 2006-09-10
So, when I install programs from the synaptic package manager, most of the time I can go to either applications, system/preferences or system/administration (graphically) and i will see the program that I just installed.  A few of them however, do not show up.  I am guessing they are accessable throught the command line, but I don't have the faintest idea how to start them up that way.

I have dug around quite a bit, but this question seems to be too simple to warrant much explaination, so I post here.

Any ideas on how to get a master list of the programs on my dapper system,graphically or command line wise?  I am guessing there is a menu command, and from there I could track down these wayward applications I have installed, but have not seen hide nor hair of.

Thank you, community!

---

### Post by emprog on 2006-09-10
Usually you can just enter the name of the application. For example in terminal you can enter firefox to run firefox browser, or gaim to launch gaim messenger etc.

---

### Post by jordanmthomas on 2006-09-10
Nah, it's not a dumb question.
You need to install the Debian Menu -- it has a LOT more programs listed on it than the default gnome ones.
```
sudo apt-get install menu
```

Also, most programs can be found in /usr/bin id you want to poke around in there.

---

### Post by George_S on 2006-09-10
> **dolphinsonar said:**
> A few of them however, do not show up.  I am guessing they are accessable throught the command line, but I don't have the faintest idea how to start them up that way.


One way to find where a given program is located is to type the following into the command prompt:

```
whereis [program name]
```

For example, on my system this request:

```
whereis skype
```

.. results in:

```
skype: /usr/bin/skype /usr/lib/skype /usr/bin/X11/skype /usr/share/skype
```

---

