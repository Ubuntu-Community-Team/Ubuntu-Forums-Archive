---
title: "Error when I try to install programs"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by jonsayer on 2007-08-28
I am unable to install any programs using the install/remove application. I get this error when I do?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What does this mean and how do I fix it?

---

### Post by Marat Galiev on 2007-08-28
Maybe reinstall you dpkg package?:)

---

### Post by nemequ on 2007-08-28
It means dpkg was interrupted before finishing a previous action. To fix it, run 'dpkg --configure -a'.

---

### Post by lisati on 2007-08-28
I've had similar messages,\ in the past but can't remember exactly what I did to get round them. What happens when you type in:
```
dpkg --configure -a
```
It might provide us with a clue how to advise you.

---

### Post by jonsayer on 2007-08-28
well, I did that and terminal didn't tell me anything. Now when i click on a program in install/remove, all I get is a spinny wheel cursor that won't stop

---

### Post by Dark Star on 2007-08-28
> **lisati said:**
> I've had similar messages,\ in the past but can't remember exactly what I did to get round them. What happens when you type in:
```
dpkg --configure -a
```
It might provide us with a clue how to advise you.
```
sudo dpkg --configure -a
```
then do an update for the system
```
sudo apt-get install -f
sudo apt-get update
```

---

### Post by jonsayer on 2007-08-28
I think i found a problem:

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

I get this after I run the second command in the last post (sudo apt-get install -f) 

i remember trying to install virtualbox once, but I never got it to work so i gave up on it.

is this the source of my problem?

---

### Post by jonsayer on 2007-08-28
Problem solved! I went to virtual box's website and installed the bloody thing!

Now everything works... except for virtualbox of course.

oh well. that's another post for another day

---

