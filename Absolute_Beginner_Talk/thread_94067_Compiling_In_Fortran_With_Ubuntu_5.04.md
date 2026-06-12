---
title: "Compiling In Fortran With Ubuntu 5.04"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by NiTsi on 2005-11-23
PLEASE SOMEBODY HELP ME.
HOW CAN I COMPILE A TEXTFILE (e.g. sort.f) IN FORTRAN WITH UBUNTU 5.04?
I CAN'T FIND G77 AQND I DON'T KNOW WHAT TO DO

---

### Post by kperkins on 2005-11-23
apt-get install g77
(or open up synaptic search for g77 and install it from there) 
fortran and g77 aren't installed by default.
(and please stop shouting--it's not the end of the world :D)
whoops just saw that you are using Hoary not sure what repository it's in there, but you may want to enable universe, and multiverse, if you haven't done that already

---

### Post by Brunellus on 2005-11-23
Have you added the universe and multiverse repositories yet?

Follow these directions:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

then install via synaptic (System>Administration>Synaptic Package Manager)

Last I checked, you can also use lowercase letters when posting stuff on these boards.

---

