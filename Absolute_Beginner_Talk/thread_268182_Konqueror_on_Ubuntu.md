---
title: "Konqueror on Ubuntu?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Frak on 2006-09-29
Is there any way to install Konqeror on Ubuntu?

---

### Post by DirtDawg on 2006-09-29
cant you just use synaptic?

---

### Post by Frak on 2006-09-29
Didnt think of that Ill try it when my add/remove gets done

---

### Post by click4851 on 2006-09-29
you may see synaptic asking to install some additional KDE stuff in support of Konqureor, but yeah it should be available.

---

### Post by kerry_s on 2006-09-29
Yep, just->

sudo apt-get install konqueror

I'm using it in openbox as my desktop,file manager,web browser and what ever else i can get it to do.

---

### Post by airtonix on 2006-10-03
mmmm, seems that the latest security update has left me hanging in the breeze....

I tried 
```

:~$ sudo apt-get install konqueror konqueror-nsplugins

```but it gave me : 
```

The following packages have unmet dependencies:
  konqueror: Depends: kdesktop (= 4:3.5.2-0ubuntu26) but it is not going to be installed
E: Broken packages

```

So i tried to find out more by doing : 

```

:~$ sudo apt-get install kdesktop

```

and this gave me : 

```

The following packages have unmet dependencies:
  kdesktop: Depends: kdebase-bin (= 4:3.5.2-0ubuntu26) but 4:3.5.2-0ubuntu27 is to be installed
E: Broken packages

```

---

### Post by aysiu on 2006-10-03
Dependency problems generally stem from bad sources.lists

Step 1. Get a fresh sources.list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Step 2. Install Konqueror ```
sudo aptitude update && sudo aptitude install konqueror
``` Use *aptitude* instead of *apt-get*--[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

