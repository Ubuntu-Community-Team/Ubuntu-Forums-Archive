---
title: "Downloading Pidgin"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Armman on 2007-08-19
Last time i installed pidgin I didn't have to compile it from source. But I can't remember where I got it. Anyone know a link where I can download pidgin without compiling it from source?:confused:

---

### Post by Ek0nomik on 2007-08-19
[http://www.getdeb.net/release.php?id=1209](http://www.getdeb.net/release.php?id=1209)

By the next Ubuntu release the following will work:

```
sudo apt-get install pidgin
```

---

### Post by Armman on 2007-08-19
Thanks! :)

---

### Post by Ek0nomik on 2007-08-19
> **Armman said:**
> Thanks! :)

Anytime.  :)

---

### Post by antharr on 2007-08-19
What repository is required to install Pidgin?

---

### Post by Ek0nomik on 2007-08-19
You need to use the Gutsy repository.

---

### Post by Hobo Joe on 2007-08-20
> **Ek0nomik said:**
> You need to use the Gutsy repository.

I got pidgin through a Feisty repository, but it was so long back that I can't remember where I got it, but the repo's are:
```

##Pidgin
deb http://apt.schmidtke-hb.de/ feisty main
deb-src http://apt.schmidtke-hb.de/ feisty main

```

---

### Post by antharr on 2007-08-20
Thanks for the prompt response guys. I love this forum!!!!!:)

---

### Post by jusmurph on 2007-08-20
Just use get-deb...

Its so much easier, 3rd party repos can get messy.

---

### Post by antharr on 2007-08-20
I am not familiar with the get-deb command and if it keeps my sources.list file nice and tidy I will use it. Do you use the it same as get-apt?

---

### Post by sumguy231 on 2007-08-20
> **antharr said:**
> I am not familiar with the get-deb command and if it keeps my sources.list file nice and tidy I will use it. Do you use the it same as get-apt?

It's not a program, it's a website. See:
[http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by jusmurph on 2007-08-20
You download the data file first, then the other. Its just a heck of alot more user friendly and the fact that you can browse it is also nice.

---

### Post by antharr on 2007-08-20
Sweet. I will give that a shot. Thanks again!

---

### Post by Ek0nomik on 2007-08-20
> **Hobo Joe said:**
> I got pidgin through a Feisty repository, but it was so long back that I can't remember where I got it, but the repo's are:
```

##Pidgin
deb http://apt.schmidtke-hb.de/ feisty main
deb-src http://apt.schmidtke-hb.de/ feisty main

```

I thought he meant what official Ubuntu repo did you need.

Of course there are third party repos.  ;)

---

