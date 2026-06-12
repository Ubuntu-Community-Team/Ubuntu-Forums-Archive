---
title: "wget installation"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-07-16
hi guys for my game im making it has an updating feature this is where wget come in, i downloaded it but what commands i use to install and **what programs do i need for installation**

---

### Post by bluecherry on 2006-07-16
I dont really understand what you mean.

Are you trying to figure out how to make an installer for your game or how to create an updating utility for your game?

Easiest would be using .DEB's packages, they get updated by the Ubuntu automatically.

An easy way of creating a deb package: [http://www.falkotimme.com/howtos/checkinstall/](http://www.falkotimme.com/howtos/checkinstall/)

Hope I got your question right.

---

### Post by Ben Sprinkle on 2006-07-16
this has nothing to do with what i wanted lol i need to install the wget program, i got the source i reckon, so what things do i need before installation like gcc or something and then what do i type in command prompt to install?

its like ./configure && or something like that

---

### Post by bruce89 on 2006-07-16
> **Goat Spirit said:**
> this has nothing to do with what i wanted lol i need to install the wget program, i got the source i reckon, so what things do i need before installation like gcc or something and then what do i type in command prompt to install?

its like ./configure && or something like that

*wget* is already installed, if it isn't then do this:
```
sudo aptitude install wget
```

---

### Post by [S|G] on 2006-07-16
EDIT: Someone beat me to it :P Take a look at the post above :)

---

### Post by Ben Sprinkle on 2006-07-16
ty

---

### Post by wildseven on 2006-07-16
lol DAMN, he beat me to it!

---

