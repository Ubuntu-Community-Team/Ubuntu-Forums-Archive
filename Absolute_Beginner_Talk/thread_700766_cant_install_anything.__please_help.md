---
title: "cant install anything.  please help"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by stoneofshadow on 2008-02-18
i am a new user of ubuntu and up to yesterday i was able to install anything from the add remove menu
but now when i try to install anything i get an error message that says

E:dpkg was interupted, you must manully run 'dpkg --configure -a' to correct the problem.
E: _cache- open please report

i am the admin of this system but that dosent help
what should i do?

---

### Post by stoneofshadow on 2008-02-18
i am a new user of ubuntu and up to yesterday i was able to install anything from the add remove menu
but now when i try to install anything i get an error message that says

E:dpkg was interupted, you must manully run 'dpkg --configure -a' to correct the problem.
E: _cache- open please report

i am the admin of this system but that dosent help
what should i do?

---

### Post by jan quark on 2008-02-18
run 

```
sudo dpkg --configure -a
```

and see if this helps

---

### Post by Shadowmeph on 2008-02-18
I am a total noob but I would try and copy paiste that command into the terminal and go from there ('dpkg --configure -a)

---

### Post by Partyboi2 on 2008-02-18
try what Shadowmeph said if you have not already done so, open up a terminal (Applications>Accessories>Terminal)  make sure you have sudo before the command so that it gives your admin privileges to execute the command, so 
```
dpkg --configure -a
```
should be
```
sudo dpkg --configure -a
```

---

### Post by stoneofshadow on 2008-02-18
oh
apperently all i had to do was put sudo in front of that dpkg 
thanks partyboi2

---

### Post by stoneofshadow on 2008-02-18
yep that was all i needed
it seems to be working but it did say a message that i have 1 broken filter
is that important?

---

### Post by JoshuaRL on 2008-02-18
Yes it is.  Go to System->Administration->Synaptic Package Manager.

Then go to filters and look for the one that says "broken".  Click all those there for reinstallation and hit the Apply button.  Let it do it's thing and it should be fixed.

---

### Post by stoneofshadow on 2008-02-18
now it ways 0 broken in that menu that you told me to go to
weird

---

### Post by JoshuaRL on 2008-02-18
Try this in the terminal:
```

sudo apt-get install -f

```

---

### Post by lam2988 on 2008-03-03
hi, i also am having this problem but when i go to the application>acc>ter and type in sudo dpkg--configure-a i get a message that said it was invalid. am i typing the command in the wrong place please advise.:(

---

### Post by bulmer247 on 2008-03-03
i had this problem but it would not let me run the comand due to a SUPERUSER THING SO I SAVED EVERY THING TO A PEN STICK AND REINSTALLED UBUNTU THE PUT MY FILES BACK ON NOW IT WORKS GREAT

---

### Post by Duck2006 on 2008-03-03
Not

sudo dpkg--configure-a

but

sudo dpkg --configure -a

Don't forget the spaces.

---

