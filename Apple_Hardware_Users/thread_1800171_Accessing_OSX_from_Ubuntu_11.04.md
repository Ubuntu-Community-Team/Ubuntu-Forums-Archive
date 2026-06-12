---
title: "Accessing OSX from Ubuntu 11.04"
date: 2011-07-08
forum: Apple Hardware Users
---

### Post by alirath2212 on 2011-07-08
Hey, 
So I recently downloaded ubuntu 11.04 and have it running alongside OSX on my Macbook Pro. I'd like to access the files (specifically music) on the OSX partition. How would I go about doing this? Thanks!

---

### Post by johnmurrayvi on 2011-07-08
Sorry I can't give a longer reply right now as I'm about to leave, but this link should be useful:

[http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)

---

### Post by stewacide on 2011-07-08
The key point is to match your UID in OSX and Linux (see link above). After that you should be able to access your Mac files no problem.

---

### Post by alirath2212 on 2011-07-09
So after following said website, I was able to find the folders from ubuntu but it said I didn't have the permissions to access them. Any idea what I did wrong? Thanks so much!

---

### Post by DoubleClicker on 2011-07-09
did you make sure you had the same UID (user ID) for Ubuntu and Mac OSX?   by default mac UID start at 501 and Ubuntu UID start ay 1001. For example if your username is Foo in ubuntu with a UID of 1001, and your username is Bar (it doesnt really matter what the username is)  in macOSX with a UID of 501 you need to do is set your UID to 501

```
sudo  bash
``` (you need to be in a root terminal, don't sudo each command)

```
gedit /etc/passwd 
```


change: 
```
foo:x:1001:1001:Ima Foo,,,,:/home/foo:/bin/bash
```

to
```
foo:x:501:501:Ima Foo,,,,:/home/foo:/bin/bash
```

then

then do 
```
chown -R 501:501 /home/foo
```

Please substitute your real username for Foo, and don't actually type Foo unless that is your real username:lolflag:

---

### Post by alirath2212 on 2011-07-09
Yes, the uid's are the same. (I just double checked). What should I check next? The folders are there, they just have the little 'x' over them.

---

