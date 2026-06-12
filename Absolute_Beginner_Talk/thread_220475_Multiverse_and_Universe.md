---
title: "Multiverse and Universe"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by rene100 on 2006-07-21
Everytime I check multiverse and universe in software properties, and then reload, When I go back they are unchecked....  Does anyone know why?

---

### Post by Dr. Nick on 2006-07-21
Dont know why, but you can enable them by editing the configuration file

/etc/apt/sources.list

Run from a terminal

gksudo gedit /etc/apt/sources.list 

read the file and it will tell you to remove 2 #'s to enable the universe/multiverse repos, Remove them then save and exit. 

Then either hit reload in synaptic, or run

sudo apt-get update

---

### Post by anothernoob123 on 2006-07-21
Why do people do this? What dose this cause?

---

### Post by trent dillman on 2006-07-21
try

```
gksudo gedit /etc/apt/sources.lst
```

then uncomment (delete the #) in front of the multi/universe lines

or, search the forums for bumps :-)

EDIT: Nick beat me to it...

---

### Post by rene100 on 2006-07-21
I removed the comments.  Strange though under software properties the universe and multiverse settings still appear unchecked.

---

### Post by Jagot on 2006-07-21
Use this guide:

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by fatsheep on 2006-07-21
Does that for me too but I think you only have to check them once since I have installed Sun Java from the repositories and that is multiverse.

---

### Post by Dr. Nick on 2006-07-21
> **anothernoob123 said:**
> Why do people do this? What dose this cause?


Why do people do what? Enable universe,multiverse? Enabling them will open up more software for installation, Stuff that for one reason or another could not be included by default

---

### Post by Jagot on 2006-07-21
You can read more about the repos here:

[http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

---

### Post by trent dillman on 2006-07-21
maybe someone should file a bug report? I just checked, and mine are checkmarked in the gui...

---

