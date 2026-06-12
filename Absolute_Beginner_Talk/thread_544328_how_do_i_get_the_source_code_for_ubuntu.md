---
title: "how do i get the source code for ubuntu"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by semeretaddis on 2007-09-06
hello every one my name is semeret addis. i'm new to this forum. and i'm a computer science student at a university in Ethiopia. i'm also a last year student.you see i had a 3 days training on linux from an organization called "EFOSSNET".actually i did work on linux in my operating system class. but i become so interested in linux after the training from EFOSSNET. specially on one of it's distribution that is ubuntu. i want to practice on ubuntu .i also want to change the features of ubuntu. but i couldn't find the source code. i tryed to to find it on the internet but it seems impossible for me till now. so if anyone can tell me or informe me on how to find it , i would appreciate your help. or u can even send me the code through my email. [email]free10sem@yahoo.com[/email]. thank you

---

### Post by mxg01 on 2007-09-06
Ubuntu is made up of lots of different parts. You can get the source for each part but not a total bundle of source (I don't think so anyway).

So if you want the source for a particular package do this:

sudo apt-get build-dep package_name
sudo apt-get source package_name

That will give you the source for that package.

Remember that lots of thing are configurable anyway just using the options available.

---

### Post by por100pre1 on 2007-09-06
In:

```
gksu software-properties-gtk
```

Add a check mark to **Source Code**

Then use Synaptic for some nice source code hunting. :)

---

