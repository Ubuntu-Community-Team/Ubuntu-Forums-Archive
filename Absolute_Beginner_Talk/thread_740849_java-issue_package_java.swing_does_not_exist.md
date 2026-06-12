---
title: "java-issue: package java.swing does not exist"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by GnuensFar on 2008-03-31
Hey. I've installed sun-java6-jdk on 7.10, and simple code works just fine.

But when i try to do a: import java.swing.*; it tells me package java.swing does not exist.

Im using emacs and terminal. Can anyone please tell me what im doing wrong?

---

### Post by GnuensFar on 2008-03-31
Actually i'll answer myself.. It's supposed to be javax.swing:confused:

---

### Post by neurostu on 2008-03-31
Thats right you have:
java.awt 
&
javax.swing

Its a common mistake.

---

