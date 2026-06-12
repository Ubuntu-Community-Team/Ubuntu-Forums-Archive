---
title: "How do I install a Linux .run file - I've no clues."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by wapfu on 2007-06-28
hi,
i have quake4-linux-1.4.2x86.run file on a CD.
How do I install it?
is it possible?
I've double clicked on it, used the synaptic file manager, tried the add/remove , tried to use the terminal - all to no avail.
Couldn't find help on google - maybe asking the wrong question?
Its on cdrom0.

Lost without a clue.

Thanks 
Bill

---

### Post by nocturn on 2007-06-28
> **wapfu said:**
> hi,
i have quake4-linux-1.4.2x86.run file on a CD.
How do I install it?
is it possible?
I've double clicked on it, used the synaptic file manager, tried the add/remove , tried to use the terminal - all to no avail.
Couldn't find help on google - maybe asking the wrong question?
Its on cdrom0.

Lost without a clue.

Thanks 
Bill

I'm not 100% sure.  But you could copy it to HD, set execute permission in the permissions page (or chmod +x in terminal).

Then try to run it again.

---

### Post by RomeReactor on 2007-06-28
Hi. To install it from the terminal (you'll need to navigate to the file's location first, or copy the file to your system and set it as executable, as **nocturn** said):
```
./quake4-linux-1.4.2x86.run
```

---

### Post by Tricore on 2007-06-28
IIRC .run is some kind of script. Try

```
sudo sh quake4-linux-1.4.2x86.run
```

from terminal, when you're in the directory.

---

### Post by wapfu on 2007-06-28
Cheers,
Best regards
Bill

---

