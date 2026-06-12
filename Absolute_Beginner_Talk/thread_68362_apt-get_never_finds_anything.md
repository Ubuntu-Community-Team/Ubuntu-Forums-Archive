---
title: "apt-get never finds anything?"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by ddemers on 2005-09-22
E: couldnt find package. <-- this is the error I have gotten everytime Ive tried to use the command.  

Ive been looking around, seen some references to editing the sources.list file.. however it keeps telling me I am not the owner and cannot edit it..,,

My guess is I have to add certain servers to this file (located in /etc/apt), so does anyone have a list of the most common ones?

And how can I edit this list?

---

### Post by John.Michael.Kane on 2005-09-22
these should help you 
[http://ubuntuforums.org/showthread.php?t=30147](http://ubuntuforums.org/showthread.php?t=30147)
[http://www.frankandjacq.com/ubuntuguide/5.04/index.html](http://www.frankandjacq.com/ubuntuguide/5.04/index.html)

to edit sources use sudo gedit /etc/apt/sources.list typed in terminal...


hope this helps...

---

### Post by 23meg on 2005-09-22
you can edit the file by typing "sudo gedit /etc/apt/sources.list".

see also: [http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrarepositories](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrarepositories)

---

### Post by aysiu on 2005-09-22
[QUOTE=ddemers]E: couldnt find package. <-- this is the error I have gotten everytime Ive tried to use the command. [/quote] [Use Synaptic](http://www.psychocats.net/essays/winuxinstall.php)--it's the same as apt-get, only graphical, and you can see exactly what packages are available and which aren't.

> 
Ive been looking around, seen some references to editing the sources.list file..  Follow [these directions](http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories). If you're using 5.10 (Breezy), change all the *hoary* references to *breezy*, except in the backports section.

> 
however it keeps telling me I am not the owner and cannot edit it..,, You  have to ```
sudo gedit /etc/apt/sources.list
``` or, if you're using Kubuntu ```
sudo kwrite /etc/apt/sources.list
```

---

### Post by ddemers on 2005-09-22
Thanks for the info guys, also nice to know that the package manager is the same, but graphical (being a Windows admin for so many years, I tend to be a visual guy).

basically I was trying to install The Mana World and it told me to add a linkl into my sources.list.  Are there any draw backs to adding additional links?.  ie, should I add the link, download... then comment out the link again?

---

### Post by aysiu on 2005-09-22
[QUOTE=ddemers]should I add the link, download... then comment out the link again?[/QUOTE] That's what I would do.

---

### Post by bored2k on 2005-09-22
I'd recommend leaving the link there. Otherwise, you will not get Mana's updates.

---

