---
title: "hello all"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by pmn.blazer on 2007-11-18
which one i download for ubuntu6.06 for java...please tell me
your best regards
blazer

---

### Post by oilchangeguy on 2007-11-18
> **pmn.blazer said:**
> which one i download for ubuntu6.06 for java...please tell me
your best regards
blazer

before you click submit, read your post to see if it makes sense. because this one does not. if english is not your first language, there are many non-english forums.

---

### Post by pmn.blazer on 2007-11-18
my fri sorry for my poor english :(
I want to know about how can i compile for java.....
:)

---

### Post by overdrank on 2007-11-18
> **pmn.blazer said:**
> which one i download for ubuntu6.06 for java...please tell me
your best regards
blazer

HI and maybe this will help
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)
Good luck! :KS

---

### Post by pmn.blazer on 2007-11-18
no fri...
I mean in outside....u know as in terminal....
javac....
java.....
for .java...
:(................language problem???:(

---

### Post by oilchangeguy on 2007-11-18
> **pmn.blazer said:**
> no fri...
I mean in outside....u know as in terminal....
javac....
java.....
for .java...
:(................language problem???:(

what is your first language?

---

### Post by Arthur Archnix on 2007-11-18
Hey oilchange guy, you want to correct grammar go to an English help support forum. We're here to talk about Ubuntu.

---

### Post by overdrank on 2007-11-18
> **pmn.blazer said:**
> no fri...
I mean in outside....u know as in terminal....
javac....
java.....
for .java...
:(................language problem???:(

[http://java.sun.com/j2se/1.4.2/docs/tooldocs/windows/javac.html](http://java.sun.com/j2se/1.4.2/docs/tooldocs/windows/javac.html)

:confused:

---

### Post by pmn.blazer on 2007-11-18
fri u got something wrong 
i think 
i am not talking like that ok???
and also i am not idiot a t all.....
u shouldn't tell like that ok????
:(

---

### Post by pmn.blazer on 2007-11-18
now i only want to know about 
how can i run java...and javac

---

### Post by oilchangeguy on 2007-11-18
> **pmn.blazer said:**
> fri u got something wrong 
i think 
i am not talking like that ok???
and also i am not idiot a t all.....
u shouldn't tell like that ok????
:(

i'm not calling YOU an idiot, but the fool who said something about me asking you about what language you spoke.

---

### Post by pmn.blazer on 2007-11-18
what is that????
i want to know which jvm to run........ng 
kk???
something wrong???????/this room??

---

### Post by twisted_steel on 2007-11-18
I believe you are looking for the Sun JDK (Java Development Kit).  If you want to run applications instead of compiling them, you would need the Sun JRE (Java Runtime Environment).

There are two versions that I can see in the repositories - Java 5 and Java 6.  There might be some deprecated functions in the newer version, but I would give Java 6 a try first.

You will need to enable the multiverse repository: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu).  If you are using Gutsy, the windows may look a little different, but the one you want to check says "Software restricted by copyright or legal issues (multiverse)"

After that, either look in the Synaptic package manager for sun-java6-jdk, or use the terminal:

```
sudo apt-get install sun-java6-jdk
```It looks like this will also install the JRE for you.

---

