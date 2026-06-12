---
title: "Restricted-Extras problem and others! :]"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-04-04
HellO!
So basically when trying to install the restricted extras with the command:

```
sudo apt-get install ubuntu-restricted-extras
```

the terminal spits out:

```
han@han-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for han:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
han@han-laptop:~$ 

```

Any clues? ^.^

---

### Post by neurostu on 2008-04-04
There isn't a package entitled "ubuntu-restricted-extras".

There is a repository with a similar name.  Are you trying to enable that repository?

---

### Post by FuturePilot on 2008-04-04
> **neurostu said:**
> There isn't a package entitled "ubuntu-restricted-extras".

Yes there is.

Go System&#8594;Administration&#8594;Software Sources and check all of the boxes in the first tab. Uncheck the CD-ROM if it is checked. Go to the Updates tab and check the first two boxes and optionally the fourth (for the backports). Click Close and then Reload when prompted. Then try to install the restricted-extras again.

---

### Post by neurostu on 2008-04-04
Ok so I guess I was wrong:
```

aptitude search ubuntu-restricted

```
gives:
```

p   kubuntu-restricted-extras       - Commonly used restricted packages         
p   ubuntu-restricted-extras        - Commonly used restricted packages         
p   xubuntu-restricted-extras       - Commonly used restricted packages         

```
I would suggest you check your spelling or paste this exact command:
```

sudo apt-get install ubuntu-restricted-extras 

```

---

### Post by nick_h on 2008-04-04
Open System->Administration->Software Sources and check that you have the multiverse repository enabled.

---

### Post by hungryOrb on 2008-04-04
ohoh, thankyou so much :) works perfectly of course!

<3<3<3

---

