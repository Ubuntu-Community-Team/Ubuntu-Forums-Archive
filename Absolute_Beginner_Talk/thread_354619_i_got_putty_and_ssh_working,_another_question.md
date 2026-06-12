---
title: "i got putty and ssh working, another question"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2007-02-06
I have ssh and putty working and I can connect to my machine outside my network.  Now what if I'm at say school and I want to hear the sound from xmms on my laptop, is this possible?

---

### Post by jd65pl on 2007-02-06
You can tunnel X over ssh so yes it is possible. you would do the following

```
ssh -X myUser@myServer
```

Then Log on and do

```
xmms
```

---

### Post by borris.morris on 2007-02-06
Yes, use the teminal manager under Applications -> Internet -> Terminal Server Client,  oh wait. Your using ssh. I was thinking about VNC. My bad.

---

### Post by Josh1 on 2007-02-06
If you own the laptop, just setup streaming on port 80.. if the laptop is the school's, stream on port 80 as well.

I use to get like 200 connections at once and it crashed my internet since it was only 256 UP. Ended up closing it after getting in trouble.

---

### Post by zetsumei on 2007-02-06
how can i stream on port 80? im on the windows laptop right now...and im using putty

---

### Post by borris.morris on 2007-02-06
that would be pretty sweet. 200 connections. be nice to get to my laptop at school. or my desktop.

---

### Post by Saatii on 2008-02-26
check [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Using_SSH_to_Port_Forward](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Using_SSH_to_Port_Forward)

---

