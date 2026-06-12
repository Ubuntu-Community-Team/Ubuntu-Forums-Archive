---
title: "Ktorrent won't load"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by jtb108 on 2008-02-29
Hello,

I am using Feisty Fawn 7.04 and have downloaded and installed all the updates.

KTorrent just stopped working yesterday. I have used it successfully for about one year.

I tried to load it about fifteen times and it won't load. I used it with an unknown wireless network in New York last night and now it has stopped working.

I deleted KTorrent and reinstalled it using ADD/REMOVE but even though it shows up in the Applications menu it won't load when I click on it.

The system monitor shows Ktorrent 9487 and 9488 as "sleeping" when I click on KTorrent to load it. After about 20 seconds the two files disappear from the system monitor.

I am hopeful that somebody has an idea what's happening.

Thank you,

John B.

---

### Post by y-lee on 2008-02-29
I don't know but whenever programs don't work right start them in a terminal and see what error messages they give

```
ktorrent
```


Post any error messages here and that might help :)

---

### Post by jtb108 on 2008-02-29
Thank you for the suggestion.

Here is was comes up when I type in Ktorren:

:~$ ktorrent
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/john192/.DCOPserver_john192-laptop__0
and start dcopserver again.
---------------------------------

DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
WARNING: DCOP communication problem!
kdeinit: Communication error with launcher. Exiting!


John B

---

### Post by y-lee on 2008-02-29
that is a little beyond me but googling it found several possible solutions. The simplest was to try the code below:

```
dcopserver_shutdown
kdeinit
```

I'm not sure if one needs to do this as superuser or not so try it as is, if that don't work try it with **sudo**. Now try ktorrent.

btw are you in gnome or kde or something else?

---

### Post by jtb108 on 2008-02-29
When I type in the following:

dcopserver_shutdownet
kdeinit

I get this:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!

Thank you for the suggestion. I somehow feel that the wireless I used in New York fouled something up.

John B

---

### Post by y-lee on 2008-02-29
Ktorrent still doesn't work I take it?

Try [dcopserver problems]("http://ubuntuforums.org/showthread.php?t=687457")

Hmm ```
kio (KSycoca): ERROR: No database available!
```

This error concerns me. Not sure why ya are getting that one.

---

### Post by bratliff on 2008-03-03
This is the message when I do the below command. 
dcopserver_shutdown
bob@bob-desktop:~$ kdeinit
Only one line in dcopserver file !: 
DCOPClient::attachInternal. Attach failed networkIdsList argument is NULL
Only one line in dcopserver file !: 
DCOPClient::attachInternal. Attach failed networkIdsList argument is NULL
DCOPServer self-test failed.
kdeinit: DCOPServer could not be started, aborting.

When I start Krusader I get this message: decopserver not running.
HELP........................

Bratliff




> **y-lee said:**
> that is a little beyond me but googling it found several possible solutions. The simplest was to try the code below:

```
dcopserver_shutdown
kdeinit
```

I'm not sure if one needs to do this as superuser or not so try it as is, if that don't work try it with **sudo**. Now try ktorrent.

btw are you in gnome or kde or something else?

---

