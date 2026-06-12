---
title: "configure: error: no acceptable C compiler found in $PATH"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by anubis2814 on 2006-07-11
How do I fix this error, I can't install several programs because of this

---

### Post by anubis2814 on 2006-07-11
BTW I am using Ubuntu 6.06

---

### Post by Kilz on 2006-07-11
> **anubis2814 said:**
> BTW I am using Ubuntu 6.06
```
sudo apt-get install build-essential
```
Just a question, are you building the applications because they are not avaiable in syanaptic?

---

### Post by anubis2814 on 2006-07-11
I am trying to install a CD/DVD burning program and they all how up with that error message when i try to install

---

### Post by digby on 2006-07-11
Which program is it?

---

### Post by anubis2814 on 2006-07-11
k3b or gnomebaker, no luck installing either
the instructions say i should type make, but it says it doesn't compile

---

### Post by digby on 2006-07-12
I thought that gnomebaker was included with the default install, but I could be mistaken.  In any case, it's available in the repositories, so there's no need to go through the hassle of compling it.  You can install it w/```
sudo apt-get install gnomebaker
```

---

### Post by SigmaX on 2006-07-12
Have you discovered adept yet?  It'll show you in an instant the power of apt-get.  You'll rarely have to compile from source, adept/apt-get will handle all your software for you automagically.

SigmaX

---

### Post by phegdepatil on 2007-07-12
facing the same error after ./configure  configure: error: no acceptable C compiler found in $PATH. Unable to get command sudo apt-get install build-essential as it cannot find the build-essential package. What else can be done ? Please help.

---

