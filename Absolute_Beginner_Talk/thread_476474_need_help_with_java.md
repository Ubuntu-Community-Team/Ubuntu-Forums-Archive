---
title: "need help with java"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by axemurder785 on 2007-06-17
I am having a huge amount of trouble with installing java and getting it to work on fire fox please help me!

---

### Post by Tasu on 2007-06-17
O_O Well, could you please be more specific on the problem? describe it bettere.. did you installed from synaptic or from the packages on th sun's website?

---

### Post by axemurder785 on 2007-06-17
i downloaded the file jre-6-linux-i586.bin from the sun website

---

### Post by Lord Illidan on 2007-06-17
Basically, it is just a question of installing it from synaptic/apt-get

```
sudo aptitude install sun-java6-jre
```

---

### Post by axemurder785 on 2007-06-17
it said couldn't find any package whose name or descriiption matched "sun-java6-jre"

---

### Post by dpar on 2007-06-17
You must enable the resricted repos.

---

### Post by axemurder785 on 2007-06-17
what does it mean that my computer is i386?

---

### Post by steve.horsley on 2007-06-17
IN Synaptic, go Settings->Repositories nd then tick the multiverse, universe and restricted repositories. OK this, and then click the reload icon on the main page, to get the new indexes. Now you will be able to find sun-java6-jre. This is easier than installing Sun's stuff independently.

---

### Post by dpar on 2007-06-17
Start Synaptic package manager. System>Administration>Synaptic Pacage Manager
Click on Settings
Click on Repositories
Under Ubuntu Software, make sure the top 4 have checkmarks
Click ok
Click reload
Your done:D

---

### Post by dpar on 2007-06-17
Arrrggggg, beat me!!

---

