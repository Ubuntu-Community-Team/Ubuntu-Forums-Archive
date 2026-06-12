---
title: "help topics blank page?..."
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by charsiubao on 2005-12-27
i couldnt find anything about this problem...
when i click on the help topics button (the lifesaver)...i only a get a blank page.  i know what it should look like (has manual, starter guide, etc) b/c i have it on my laptop...anyway to get around this??

---

### Post by d1337 on 2005-12-27
Make sure that ubuntu-docs is installed on your machine.  You should be able to do this via apt
```
sudo apt-get install ubuntu-docs
```
or using synaptic package manager by searching ubuntu-docs, check the box and apply.  Post back as this is part of the typical/default install and I'd like to know if something has gone afoul.

d1337

---

### Post by charsiubao on 2005-12-27
i tried both methods...
first, with terminal -- says that there is no need to update
second, with synaptic -- i marked for re-installation (as it said it was already installed) and had to use the install cd.

rebooted after each time, hoping that might help...but still no dice.

to clarify...i get the header that says help topics and a picture of the lifesaver, but nothing else.

thanks~~

---

### Post by d1337 on 2005-12-28
For grins, can you see if you have "yelp" installed?  Similarly, you may use terminal or Synaptic.

d1337

---

### Post by MichaëlVD on 2006-04-03
I'm having the same problem, and I don't find a solution.

---

### Post by cvmostert on 2006-05-24
I also have the same problem ... nothing yet...

if i get it... i will post here...

ciao

---

### Post by DonS on 2006-05-25
A possible solution is to try running the command:
```
sudo scrollkeeper-rebuilddb
```

from the terminal (sorry!)

* I'm not absolutely 100% certain this the the command name, but I believe its correct.

If that doesn't work, try running
```
yelp
```
from a terminal and pasting and output it produces here.  Thanks

---

