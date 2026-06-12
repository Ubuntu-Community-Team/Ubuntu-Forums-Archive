---
title: "default program install location?"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by darckhart on 2006-04-12
sometimes when i install things it goes to:

/usr/local

and sometimes it goes to: 

/usr/local/share

how does ubuntu decide? is it sort of like an "all users" versus a "my user" thing? and if so, then should i manually install things to /usr/local/share if i want it available for everyone? thanks.

---

### Post by mandrakethepenguin on 2006-04-12
When you say install, you mean via apt-get/dpkg or from a traditional tar package?

---

### Post by darckhart on 2006-04-12
either way doesn't really matter since the program files will end up in those locations i believe, but for simplicity's sake let's say apt-get.

---

### Post by mandrakethepenguin on 2006-04-12
The people who compile the .deb (apt-get) packages specify where the files will be installed.  I'm pretty sure that if you install packages with apt-get by terminal or if you use Synaptic, the programs you install are available for all users.

---

