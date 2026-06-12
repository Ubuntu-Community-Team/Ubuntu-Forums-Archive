---
title: "I Cant get frost wire to work!!"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by macneil on 2006-08-17
hey all,
im new to ubuntu i tried to get frostwire and for some reason it wont open.. can any one help me?

---

### Post by magnoliablossom on 2006-08-17
in terminal type

which frostwire

then when it gives you the directory, copy and paste that back in terminal and see what it tells you.

edit:

Also, be sure you've installed java....And that it's configured right.  I had to do this to get it to work:

sudo update-alternatives --config java

then selected the 3rd option.

---

### Post by taurus on 2006-08-17
Do you have java on your machine and try to run it from a terminal so you know what the error message is?  Open a terminal with Application -> Accessories -> Terminal and type

```
frostwire
```

---

### Post by macneil on 2006-08-17
hey, it says i need "JRE" java client i downloaded the newest java tho and nothing happens..

---

### Post by magnoliablossom on 2006-08-17
ok, then in terminal just to be sure it's installed properly type

java -version    <<---that should tell you which version you have installed.

if it's not, try installing it with [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_use_Easy_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_use_Easy_Ubuntu)

---

### Post by macneil on 2006-08-17
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

is that the right version?

---

### Post by taurus on 2006-08-17
> **macneil said:**
> java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

is that the right version?
NOPE!!!  That is the one from gcc which is as far as I know, a piece of crap...  You need to configure your system to use the one that you have installed.

---

### Post by macneil on 2006-08-17
that is the one that i got off ubuntuguide.org 
can someone get me the right version please;-)

---

### Post by magnoliablossom on 2006-08-17
just use this and it'll install the right one:

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_use_Easy_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_use_Easy_Ubuntu)

and be sure to this afterwards:

sudo update-alternatives --config java

then selected the 3rd option.

---

### Post by taurus on 2006-08-17
Use Automatix and install java (the real one) then...

---

### Post by macneil on 2006-08-17
thanks for the help every one
Cheers

---

