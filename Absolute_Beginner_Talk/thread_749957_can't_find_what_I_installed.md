---
title: "can't find what I installed"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by harryliddic on 2008-04-09
I installed kdepim, it shows green in the synaptic, but I can't find it.

---

### Post by tamoneya on 2008-04-09
Alt-F2```
kdepim
```
That should start the program for you.

---

### Post by ramjet_1953 on 2008-04-09
You can also use this method:

1. Open a terminal by navigating to:  [COLOR="Blue"]Applications>Accessories>Terminal[/COLOR]

2. type in this [COLOR="Blue"]whereis <name of what you are looking for>[/COLOR]

Regards,
Roger :cool:

---

### Post by harryliddic on 2008-04-09
i got this cryptic response

harry@harry-desktop:~$ kdepim
bash: kdepim: command not found
harry@harry-desktop:~$ whereis kdepim
kdepim:
harry@harry-desktop:~$

---

### Post by swoll1980 on 2008-04-09
go to system>admistration>synaptic do a search for kdepim when you find it right click it hit properties then installed files it will tell you were it was installed look for the .bin
or try alt-f2     
         /usr/bin/kdepim thats were most of them go

---

### Post by hvac3901 on 2008-04-09
alt f2 is something i didn't know yet...good to know. thanks

---

### Post by ramjet_1953 on 2008-04-09
kdepim may not be the actual executable file.

A way to check this is to open the [COLOR="Blue"]Synaptic Package Manager[/COLOR].

When it opens, click on[COLOR="Blue"] Settings>Preferences[/COLOR]

When the menu opens, make sure that there is a[COLOR="Blue"] tick in Show Package Properties in Main Window[/COLOR]. Click on [COLOR="Blue"]Apply then OK[/COLOR].

Now click on [COLOR="Blue"]Search[/COLOR] and enter [COLOR="Red"]kdepim[/COLOR]

When it finds the package, click on it to highlight it.

Now in the lower window, you will see a series of tabs. Click on the I[COLOR="Blue"]nstalled Files ta[/COLOR]b.

It will give you a listing of files and directories where they are installed.

Look for your application. It won't be kdepim, as we have already looked for that, without success, but it may be something like kde-pim, or kdepim-desktop.

Regards,
Roger :cool:

---

### Post by sdennie on 2008-04-09
You can also do this from the command line with something like:

```

dpkg -L kdepim | grep bin

```

That should show you what files got installed in bin directories which is where executables should be placed.

---

### Post by harryliddic on 2008-04-09
I tried the synaptic and it hung on 'apply'. I also tried **dpkg -L kdepim | grep bin** and all I got was a new prompt.

---

