---
title: "apt-get command question"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by ArthurHeng on 2005-09-29
How do I make apt-get re-download the deb packages for applications I already installed? I need to store these debs in cd for other pcs without internet access, and manually download from packages.ubuntu.com is not very feasible thanks to the interlinked dependencies...

I read the apt-get help message and found the -d flag for "download only, do not install or unpack archives", but when I type "apt-get install -d someapp" it tells me the application is already installed. What should I do?

---

### Post by auburn on 2005-09-29
one of my friends once told me how to do this....I'm searching everywhere.
for starters, you can 
```
dpkg -get--selections
``` to see what packages are installed. Then you need to feed those results into some sort of download command.

---

### Post by auburn on 2005-09-29
from the dpkg man page:

 To make a local copy of the package selection states:
            dpkg --get-selections >myselections

       You might transfer this file to another computer, and install it there with:
            dpkg --set-selections <myselections
       Note  that  this will not actually install or remove anything, but just set the selection state
       on the requested packages.  You will need some  other  application  to  actually  download  and
       install the requested packages.  For example, run dselect and choose "Install".

       Ordinarily,  you will find that dselect(8) provides a more convenient way to modify the package
       selection states.

---

### Post by ArthurHeng on 2005-09-29
Thanks a lot, now for someone to tell me how to use those huge list of package names, lol.

I also need to know the command to make apt-get download those .deb packages, while I already have them installed.

---

### Post by ArthurHeng on 2005-09-29
Auburn, I really appreciate you help, but I need to download those .deb files, not just set the selections, coz Im gonna install those debs in pc **without internet access**.:(

---

### Post by auburn on 2005-09-29
I'm thinking you may have to write a short script to parse that list and feed it to wget. 

Here's someone doing something similar:

[http://lists.debian.org/deity/2005/02/msg00015.html](http://lists.debian.org/deity/2005/02/msg00015.html)

I'm afraid I don't know awk or sed yet...which I think is useful here.

---

### Post by auburn on 2005-09-29
Here's the definitive guide on such...
[http://www.batmat.net/apt-offline/ch2.html](http://www.batmat.net/apt-offline/ch2.html)

---

### Post by ArthurHeng on 2005-09-29
Ic, thanks a lot.
Now Im wonderin about apt-get **upgrade**, does it upgrade all my applications, including the already up to date ones, or just the outdated ones? Im worried about missing some debs.

---

