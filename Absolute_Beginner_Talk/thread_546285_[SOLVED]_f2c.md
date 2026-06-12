---
title: "[SOLVED] f2c"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Stebbins on 2007-09-08
How do I install f2c?

---

### Post by Tyke91 on 2007-09-08
sudo apt-get install f2c?

it's in the repos.

---

### Post by Stebbins on 2007-09-09
I tried that, but all i got was a 'package not found' message.  I also tried downloading the source and running "make", but that doesn't seem to have worked either.

---

### Post by asmoore82 on 2007-09-09
> **Stebbins said:**
> I tried that, but all i got was a 'package not found' message.  I also tried downloading the source and running "make", but that doesn't seem to have worked either.

#1. we assume you are running a modern version of Ubuntu (LTS or 7.04); is this correct?

#2. if it is a fresh install, you may need to update apt before automagically installing something ...
```
~$ sudo apt-get update && sudo apt-get install *something*
```

---

### Post by Stebbins on 2007-09-10
Yes, I am running 7.04.  Updating apt did not help my problem.  Can anyone walk me through a manual installation?

---

### Post by Perfect Storm on 2007-09-10
Enable universe and multiverse in synaptic and your package will be there.

---

### Post by Stebbins on 2007-09-10
I've never used synaptic. How do I do that?

---

### Post by Maestro23 on 2007-09-10
> **Stebbins said:**
> I've never used synaptic. How do I do that?

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Stebbins on 2007-09-10
Success! Thank you all very much for your help.

---

