---
title: "I want to write a C program"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by drcymru on 2006-06-06
Hi All
I'm brand new to Linux and Ubuntu. I've just taken possession of new laptop with Ubuntu 6 preloaded.
Now, I want to write a C program. That's not a problem.....I've dabbled in C in the past on Windows and DOS platforms.
My problem is compiling the thing.
Where would I find the C compiler on my machine (or am I being a bit daft in thinking it comes with gcc ready installed)?

any help or pointers gratefully recieved.
Thanks in advance
Dr C

---

### Post by beanlover on 2006-06-06
Ubuntu 6.06 LTS comes with gcc-4.03 I believe.

If you want other gcc versions you can apt-get them or use the gui package manager.

---

### Post by mlind on 2006-06-06
install package called build-essential. It should provide you what you need for starters.

---

### Post by drcymru on 2006-06-06
Thanks for quick responses......
I've just figured out that it maybe doesn't come with gcc installed by default and I might have to install "build essential" package.
OK...next question.......(please bare with me as I've not used Ubuntu..or other linux before).....
Where do I find "build essential" package??

Thanks again for any help

Dr C

---

### Post by IYY on 2006-06-06
It's as simple as typing:

```
sudo apt-get install build-essential
```

---

### Post by mlind on 2006-06-06
open a terminal from Applications > Accessories > Terminal
and write

```

sudo aptitude update
sudo aptitude install build-essential

```

---

### Post by drcymru on 2006-06-06
Thanks again for quick response there.
help much appreciated.
Again....I'm probably being bit dull here, but is "build-essential" a download.
I'm assuming so......

Guess all I need to do now is find myself an internet connection and figure out how to connect to it.......

Thanks
Dr C

---

### Post by mostwanted on 2006-06-06
[QUOTE=drcymru]Thanks again for quick response there.
help much appreciated.
Again....I'm probably being bit dull here, but is "build-essential" a download.
I'm assuming so......

Guess all I need to do now is find myself an internet connection and figure out how to connect to it.......

Thanks
Dr C[/QUOTE]

I think build-essential is on the install cd. Use the CD as your repository; insert it, make sure it's added to your list of repositories (it should ask you to do that if it isn't), then install build-essential.

---

### Post by drcymru on 2006-06-06
Thanks again for speedy reply.
Don't have a CD though........laptop came pre-installed.
cheers
Dr C

---

### Post by steve.horsley on 2006-06-06
[QUOTE=drcymru]Thanks again for speedy reply.
Don't have a CD though........laptop came pre-installed.
cheers
Dr C[/QUOTE]
In that case, yes you need an internet connection.

---

### Post by vdraju on 2008-07-05
[QUOTE=drcymru;1102254]Hi All
i want some programmes for practice

---

### Post by Darkchef on 2008-07-09
> **steve.horsley said:**
> In that case, yes you need an internet connection.

You could order a free CD and use that as a repository.

[https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/")

---

