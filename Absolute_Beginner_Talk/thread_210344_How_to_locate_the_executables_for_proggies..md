---
title: "How to locate the executables for proggies."
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by Frank Golden on 2006-07-06
Hi All,
   I noticed that when I use the GUI tool to configure what program to change
the default program used to open Audio Cd's or DVD movies etc. the browse
button takes you to file browser. I would like to know where most program
executables reside so I can use this browse feature to find the desired
program commands. This would help with creating launchers also.

    Not knowing where to point the browse button makes this feature 
useless for me.

---

### Post by tonyr on 2006-07-06
Most programs reside in /usr/bin, /bin, /sbin, /usr/sbin.  Some reside elsewhere like
/opt and /usr/local/bin.

I use **locate** to find a program.  It depends on a global file locator index produced
by **updatedb**.  When I want to find something I do (in a terminal)
```

sudo updatedb
locate <target-name> | grep bin

```

You can change or refine the **grep** part.

---

### Post by Kilz on 2006-07-06
[QUOTE=Frank Golden]Hi All,
   I noticed that when I use the GUI tool to configure what program to change
the default program used to open Audio Cd's or DVD movies etc. the browse
button takes you to file browser. I would like to know where most program
executables reside so I can use this browse feature to find the desired
program commands. This would help with creating launchers also.

    Not knowing where to point the browse button makes this feature 
useless for me.[/QUOTE]
Most of the exectuables are in /usr/bin some could be in /usr/local/bin, /bin, or /home/<username>/bin.

---

### Post by skirkpatrick on 2006-07-06
You can also use **whereis firefox** for example to find Firefox.

---

### Post by Frank Golden on 2006-07-06
> **skirkpatrick said:**
> You can also use **whereis firefox** for example to find Firefox.
Thanks All, that answered my question. One more related question. What is the
meaning of the switches after the program commands? For example under
multimedia tab of "Removable Drives and Media Preferences" the command for 
DVD playback is xine dvd://. What does :// do or mean? Is there a list of 
these command switches available?

---

### Post by skirkpatrick on 2006-07-07
That is not really a switch.  Switches start with a - or a -- and different switches have different meanings to different programs.  Most programs tend to use similar switches like -r for recursively traversing directories.  The **dvd://** is a parameter and tells xine to use the DVD drive to read the video.  Open a terminal and type **man xine** or **xine -h** and it'll give you all the switches and commandline parameters.  You can do this with any program.

---

### Post by Frank Golden on 2006-07-07
> **skirkpatrick said:**
> That is not really a switch.  Switches start with a - or a -- and different switches have different meanings to different programs.  Most programs tend to use similar switches like -r for recursively traversing directories.  The **dvd://** is a parameter and tells xine to use the DVD drive to read the video.  Open a terminal and type **man xine** or **xine -h** and it'll give you all the switches and commandline parameters.  You can do this with any program.Thanks

---

