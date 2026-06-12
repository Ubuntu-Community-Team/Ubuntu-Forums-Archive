---
title: "synaptic package manager not working!?!?!"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by spacebub on 2008-03-16
I'm new to ubuntu and now i'm trying to get some apps installed.  i know u can use the add/remove program or the synaptic package manager.  when i try to use either of them an error comes up saying:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have no idea what this is and what to do plz help :)

---

### Post by joshrobinson on 2008-03-16
go to applications > accesories > terminal

paste the following code 
```
sudo dpkg --configure -a
```

then try opening synaptic again

---

### Post by bsharp on 2008-03-16
Applications>Accessories>Terminal and paste 
```
sudo dpkg --configure -a
```

---

### Post by spacebub on 2008-03-16
i tried it but the same error message pops up again. 
(when the command line thing is blinking the code is done right? or should i wait a while?)

---

### Post by joshrobinson on 2008-03-16
you are typing it in with sudo in the front of it right?
so it comes up, asks for a password, you put in the password hit enter, then it should do a few things and end up back and an prompt where you can type again

---

### Post by spacebub on 2008-03-16
i found out what i was doing wrong but now i got it.  i assumed the code was done when it wasn't and x-ed out of it.  thank you so much

---

