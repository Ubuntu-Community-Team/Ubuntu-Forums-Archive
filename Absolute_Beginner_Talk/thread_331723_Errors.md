---
title: "Errors"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by wynterbourne on 2007-01-05
Recently installed Dapper Ubuntu, and decided to take a shot at installing a gmail checker. Following the directions, I had to install a perl script. I think this is the point where things went wrong. Now, when installing and uninstalling programs, I get the following error:

E: libxml-sax-perl: subprocess post-installation script returned error exit status 255
E: libxml-libxml-perl: dependency problems - leaving unconfigured
E: libxml-simple-perl: dependency problems - leaving unconfigured
E: checkgmail: dependency problems - leaving unconfigured

How can I fix this? As a note, everything seems to work but the error pops up everytime I unstall or uninstall things.:-|

---

### Post by 23meg on 2007-01-05
Try```
sudo apt-get -f install 
sudo apt-get update
```

---

### Post by wynterbourne on 2007-01-05
> **23meg said:**
> Try```
sudo apt-get -f install 
sudo apt-get update
```

Tried, still no go. Getting the error still.

---

### Post by zmuth734 on 2007-01-05
I don't know if this helps.. but..

Automatix can install checkgmail for you
Maybe uninstall what you did and let automatix do it?

---

### Post by wynterbourne on 2007-01-05
> **zmuth734 said:**
> I don't know if this helps.. but..

Automatix can install checkgmail for you
Maybe uninstall what you did and let automatix do it?

Heh, I tried that before I posted here. What I did actually was...

Install by hand (this was my mistake)
Got error
Uninstall
Install Automatix
Use Automatix to install checkgmail
Still got error
Removed /all/
Install again ... 

Still getting the error. You get the picture. ](*,)

---

