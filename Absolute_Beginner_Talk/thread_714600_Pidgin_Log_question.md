---
title: "Pidgin Log question"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by carleton97 on 2008-03-04
This is probably a really stupid question, but whatever. 

So I am truly an absolute beginner with Ubuntu/Linux. I've been running a Winbox forever, but finally bought a laptop last week. After a day of fighting with Vista at every turn, I decided to try Linux. I'm OK with tech in general and have managed to work my way various Windows versions since... Win95? This is my first real experience with anything other than Windows and I'm really loving it so far. I haven't had any problems with anything yet and if it continues, I'll be tempted to completely overwrite the partition I've got Vista hiding on. 

Anyway, I'm trying to find where my Pidgin logs are being saved (I have double checked that I have logging turned on, btw). My total unfamiliarity with the Linux file system is sort of hampering my efforts. I know from a websearch that they're here: /~.purple/log and if my googling was correct, the tilde should represent my username folder in my home directory, right? 

No luck. 

I've also searched both by the file search option and by hand through everything, but to no avail. What am I doing wrong? 

Thanks in advance for helping out the dummy!

---

### Post by Oldsoldier2003 on 2008-03-04
> **carleton97 said:**
> This is probably a really stupid question, but whatever. 

So I am truly an absolute beginner with Ubuntu/Linux. I've been running a Winbox forever, but finally bought a laptop last week. After a day of fighting with Vista at every turn, I decided to try Linux. I'm OK with tech in general and have managed to work my way various Windows versions since... Win95? This is my first real experience with anything other than Windows and I'm really loving it so far. I haven't had any problems with anything yet and if it continues, I'll be tempted to completely overwrite the partition I've got Vista hiding on. 

Anyway, I'm trying to find where my Pidgin logs are being saved (I have double checked that I have logging turned on, btw). My total unfamiliarity with the Linux file system is sort of hampering my efforts. I know from a websearch that they're here: /~.purple/log and if my googling was correct, the tilde should represent my username folder in my home directory, right? 

No luck. 

I've also searched both by the file search option and by hand through everything, but to no avail. What am I doing wrong? 

Thanks in advance for helping out the dummy!
Did you enable logging? Tools >preferences>logging

---

### Post by carleton97 on 2008-03-04
I did indeed! I tripled checked that before I posted since I didn't want to be *that* girl.

---

### Post by Sinkingships7 on 2008-03-04
the ".purple" means that the folder your looking for is hidden.

go to your home folder and go to view -> show hidden files. 

you should be set from there.

---

### Post by Oldsoldier2003 on 2008-03-04
> **Sinkingships7 said:**
> the ".purple" means that the folder your looking for is hidden.

go to your home folder and go to view -> show hidden files. 

you should be set from there.
I assumed that the logs weren't viewable from within pidgin is why I asked :)

---

### Post by carleton97 on 2008-03-04
> **Sinkingships7 said:**
> the ".purple" means that the folder your looking for is hidden.

go to your home folder and go to view -> show hidden files. 

you should be set from there.

Ahahah! Yes! That was it! 

Thank you so much!

---

### Post by carleton97 on 2008-03-04
> **Oldsoldier2003 said:**
> I assumed that the logs weren't viewable from within pidgin is why I asked :)

They aren't, but the hidden file thing was right on! 

Thank you for helping out a newbie!

---

### Post by igknighted on 2008-03-04
If you right-click a buddy and select "view log" it should show you all the conversation logs

---

### Post by xMoDx on 2008-06-11
> **carleton97 said:**
> Ahahah! Yes! That was it! 

Thank you so much!


keyboard shortcuts: CTRL + H 

this would also show hidden folders

terminal: ls -a

---

