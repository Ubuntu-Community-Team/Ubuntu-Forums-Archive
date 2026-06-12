---
title: "UPS in Ubuntu"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-10-10
Cheers,

Im planning to get a UPS, one that my Ubuntu can monitor its status, so that in case of power failure,
depending with the remaining load of the UPS lets say @ <10% load, the system will automatically 
shutdown.

And when power resumes, and the UPS is at half charge again, the system will automatically boot.

I made some inquiries and was told that the following UPS' are suitable for my hardware, and is 
capable of handling my requirements.

APC Back-Ups Pro 1000  
APC Smart-UPS 1400

However, the software for this UPS, Powerchute, I was told is for Windows only.  And since I have 
abandoned Windows as my main Home OS, my question now is that can I use either of these UPS' and 
still be able to do what I require in Ubuntu?

I am using Ubuntu 7.04

Thanks.

---

### Post by Frak on 2007-10-10
Get the SmartUPS, I've had no problems with it so far. The drivers were automatically loaded.

---

### Post by delphiguy on 2007-10-10
Do I have to install any other software? 
I'm very new at this so I'd really appreciate if any pointers/guides/howto can be given.
I dont mind going to terminal to setup things right.

thanks

---

### Post by Frak on 2007-10-10
Mine worked out of the box, also, mine is a 700 model, not a 1400.

---

### Post by Sporkman on 2007-10-10
Go into the synaptic package manager & do a search under "UPS power"... There's some interesting UPS tools in there.

---

### Post by Frak on 2007-10-10
forgot I installed the graphical UPS client
```
sudo aptitude install gapcmon
```

---

### Post by delphiguy on 2007-10-10
Thanks will this approach work with the Back-UPS???

Thanks.

---

