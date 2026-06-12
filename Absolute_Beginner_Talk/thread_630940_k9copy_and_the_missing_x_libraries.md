---
title: "k9copy and the missing x libraries"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by cameronsandiego on 2007-12-03
I am trying to configurek9copy and with the 2 newest versions i am recieving an error saying that the x libraries could not be found. this is bad for 2 reasons, i do not know where they are, and second i do not know what they are. any help would be appreciated

---

### Post by cameronsandiego on 2007-12-03
if anyone decides to try and help me, please know that i have no idea what i am doing so please be as specific as possible

---

### Post by mouseboyx on 2007-12-03
Is that exactly what it says?

---

### Post by mouseboyx on 2007-12-03
dvd95 will do pretty much the same thing as k9copy 
see if it works
```

sudo apt-get install dvd95
```

---

### Post by cameronsandiego on 2007-12-03
any tips on how to use it? i have never seen it before

---

### Post by mouseboyx on 2007-12-03
You put in a dvd and press the convert button...

---

### Post by cameronsandiego on 2007-12-03
haha, but will that copy the dvd to my hard drive?

---

### Post by cameronsandiego on 2007-12-03
it just messed upand it is frozen and will not close

---

### Post by mouseboyx on 2007-12-03
Run it in a terminal to see what the problem is
```

dvd95
```

---

### Post by p_quarles on 2007-12-03
> **cameronsandiego said:**
> haha, but will that copy the dvd to my hard drive?
First, you can get K9copy from the repos:
```
sudo apt-get install k9copy
```
It's a generally more reliable application than dvd95. For legal reasons, however, Ubuntu cannot distribute the libraries necessary to decode encrypted DVDs. You will need to get those through a third-party:
[http://medibuntu.org/](http://medibuntu.org/)

Note the explanation of the legal issues on the front page of that site.

---

### Post by cameronsandiego on 2007-12-03
in that case does anyone mind giving me some specific instruction on how i can get a dvd copied to my computer?

---

### Post by cameronsandiego on 2007-12-03
i now have k9copy and dvd95 installed...

---

### Post by p_quarles on 2007-12-03
> **cameronsandiego said:**
> in that case does anyone mind giving me some specific instruction on how i can get a dvd copied to my computer?
Go to the link I gave you, click on "repository howto", and follow the directions for the version of Ubuntu that you're using.

Then, install the correct libraries:
```
sudo apt-get install libdvdcss2
```

Then, insert the disk, open k9copy, and copy the disk.

---

### Post by cameronsandiego on 2007-12-03
it seems to be working i will let you know in a couple hours what is up. thanks for all your help guys.

---

