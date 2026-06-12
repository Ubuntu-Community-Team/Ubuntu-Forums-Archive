---
title: "how can i enforce aptitude to use always the same option"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by szymon_g on 2007-05-13
hi.
i wish i could use aptitude instead of apt-get.
but i have some irritating problem: when i do not wanna to install programs from recommends group (by default aptitude installs them: its a lot more programs then apt-get installs) i have to use following option to aptitude:

sudo aptitude --without-recommends install name_of_program

so i have a question: is any easy way to make this option default? that when i'll write : sudo aptitude install something it will make aptitude --without-recommends install something?

simon

---

### Post by zekopeko on 2007-05-13
you could make aliases in your .bash_profile so that

sudo aptitude --without-recommends install == install

look around the forums for more info

---

