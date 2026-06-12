---
title: "Can't uninstall pidgin"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-06-16
Hi guys,

I installed pidgin from source code ./configure make install...

Now, I want to uninstall it... But if I search for pidgin on synaptic is not there!  when I type 
sudo apt-get remove pidgin doesn't works...  But if I type pidgin it opens it!  
How can I uninstall it?

Thank you!

---

### Post by Kosimo on 2007-06-16
Any help?

---

### Post by skymera on 2007-06-16
hmmm pidgin was formerly Gaim...
so search see if it is called Gaim :)

---

### Post by Kosimo on 2007-06-16
> **skymera said:**
> hmmm pidgin was formerly Gaim...
so search see if it is called Gaim :)

nope :(

Is pidgin 2.0.2

---

### Post by skymera on 2007-06-16
hmmm if no more luck on here try Google.
how did u install it?

---

### Post by Ptero-4 on 2007-06-16
Kosimo. First make sure you still have the folder with the sources (where you did the make), if you deleted them, redownload (if you deleted the source tarball) them and extract them, then do the ./configure and make again (only needed if you deleted your source code folder) and then do sudo make uninstall (this step is what tracks and uninstall the copy of pidgin you installed earlier).

---

### Post by finer recliner on 2007-06-16
i believe that pidgin is not yet in the repositories (meaning that aptitude and synaptec cannot install/uninstall the application)

you will have to go to the pidgins directory and try
```

sudo make uninstall

```

---

### Post by Kosimo on 2007-06-16
> **Ptero-4 said:**
> Kosimo. First make sure you still have the folder with the sources (where you did the make), if you deleted them, redownload (if you deleted the source tarball) them and extract them, then do the ./configure and make again (only needed if you deleted your source code folder) and then do sudo make uninstall (this step is what tracks and uninstall the copy of pidgin you installed earlier).

Brilliant. That works perfectly :)  Didn't know when something is installed from source code, always need the source code to uninstall it.

Thank you again mate.

Greetings from Catalonia

Cosimo

---

### Post by Kosimo on 2007-06-16
> **finer recliner said:**
> i believe that pidgin is not yet in the repositories (meaning that aptitude and synaptec cannot install/uninstall the application)

you will have to go to the pidgins directory and try
```

sudo make uninstall

```

I needed the source code folder (make and configured) to uninstall it... It was in my bin... But still there! :) So, got into the terminal, and type sudo make uninstall ... Done :)

---

### Post by Kosimo on 2007-06-16
I have to say guys....
Ubuntu's community is amazing!
Thank you to everyone. :-o

---

### Post by skymera on 2007-06-16
i hope i helped :)

---

