---
title: "Synaptic Package Manager problems"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Evegan on 2007-06-14
While trying to install Limewire, the SPM froze up and wouldn't move nor would it close down. I restarted the computer and ever since every time I open up the package manager I get this error:
> 
E; dpkg was interrupted, you must manually run "dpkg --configure -a" to correct the problem.

E; _cache ->open () failed, please report.

Any idea what I need to do? I'm running A fresh install of Feisty.

thanks

Evan

---

### Post by shae on 2007-06-14
You should close synaptic and open the terminal. (Apps> Accessories > Terminal) and type:
```
sudo dpkg --configure -a
```

Then close terminal and open synaptic and see if the problem persists.  If it does, post here.

---

### Post by Evegan on 2007-06-14
That fixed it, just wanted to make sure I was doing the right thing before I messed something else up.

thanks

---

