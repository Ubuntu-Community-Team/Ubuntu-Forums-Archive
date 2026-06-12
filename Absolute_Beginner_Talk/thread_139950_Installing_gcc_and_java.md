---
title: "Installing gcc and java"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by jibril on 2006-03-05
hi guys

I managed to install ubuntu some days ago and installed gcc .

but when i ran a simple hello world C-code, it says cant find header files

I did
%sudo apt-get install build-essential

but that didnt work either

I also tried to compile a simple hello world java code using gij, 

but it gives me a ClassDefNotFoundException.

I then put the following like in my .bashrc 

set CLASSPATH='/home/jibril/Desktop/java'

But that didnt work either

Please Help :(

Jibril

---

### Post by Pragmatist on 2006-03-05
Give us both hello world programs (the one in C and the Java one).  Also, give the output of the following:
```
echo $PATH
```
```
java -version
```
Then type:
```
sudo updatedb
``` 
And give the output of the following:
```
locate javac
```

---

