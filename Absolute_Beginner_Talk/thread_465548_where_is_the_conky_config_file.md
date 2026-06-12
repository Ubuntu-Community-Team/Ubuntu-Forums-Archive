---
title: "where is the conky config file"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-06-05
based on this [thread]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky")
where is the conky config file arge?!

and how do i run conky in the background if i type conky in the terminal, and close that terminal it closes conky

---

### Post by taurus on 2007-06-05
You can save it to ~/.conkyrc and if you want to run it in the background, just type

```
nohup conky
```

---

### Post by steveneddy on 2007-06-05
I believe the config files for most of your applications are in your Home folder, and you can see them graphically by opening your home folder and hitting the Ctrl+H key (to show hidden files).

---

### Post by kerry_s on 2007-06-05
> **taurus said:**
> You can save it to ~/conkyrc and if you want to run it in the background, just type

```
nohup conky
```

it's ~/.conkyrc a hidden file.

---

### Post by kerry_s on 2007-06-05
> **silent1643 said:**
> based on this [thread]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky")
where is the conky config file arge?!

and how do i run conky in the background if i type conky in the terminal, and close that terminal it closes conky

use the run program.
press alt+f2 and type conky

---

### Post by steveneddy on 2007-06-05
> **kerry_s said:**
> it's ~/.conkyrc a hidden file.

Anything that has a ./name of file format - the "dot" before the slash, is a hidden file.

The ~ means it is in the Home Folder.

---

### Post by silent1643 on 2007-06-05
bah okay i figured it out.. now what is the best way to run this on startup?

---

### Post by kerry_s on 2007-06-05
put it in the startup session manger. i haven't used gnome in awhile but back when i did i had to use a script to start it after gnome, other wise gnome would cover it. if you need to do that->

gedit ~/.conky

#!/bin/sh
sleep 5
conky &

then chmod +x ~/.conky

and put that in the session startup> ~/.conky

---

### Post by silent1643 on 2007-06-06
okay cool think i got it..

i have seen the gmail option for display but is there anyway to display a pop email account in conky?

---

### Post by lazerous on 2007-06-08
Can someone help me find it too?

I looked in my home folder and I still can't find it....

ls -al  from the command line doesn't pick it up either.  Is there any other place that it would be?

[Laz]

---

### Post by wtruong on 2007-06-09
if the file is not there, that means it doesn't exist so...
gedit .conkyrc

---

### Post by diatribe on 2007-06-09
yea, by default there is no .conkyrc in your home folder, you can download one though if you google .conkyrc and there are many copies on these forums, the topic is a beatiful conky or something

---

### Post by silent1643 on 2007-06-11
yeah cool found it, topic was "post your conky config files" or something similar, got the job done and made for a good starting point

---

### Post by Seisen on 2007-06-11
Go here and just copy it from here.

[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html")

---

