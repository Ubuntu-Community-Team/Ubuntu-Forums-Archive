---
title: "C++ Help"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by mengfei on 2007-02-04
Hi there! I'm using Ubuntu for my CMPSC 201C class, and I'm having trouble. (Not with Ubuntu of course, but with the coding)

I have to make a program that will find the equation of a line that goes through two points that I input (lets call them (x1, y1) and (x2, y2)). The equation has to be displayed in the form Ax+By+C=0. From what I've got so far, A=y1-y2 and B=x2-x1. What I'm having trouble with is finding C.
I believe could find the y intercept and multiply it by -B, but I'm not sure how I could find the y intercept within the program.

Sorry if this question may seem a bit stupid, I've been studying hard all weekend and my brain doesn't seem to want to work anymore.

---

### Post by gborzi on 2007-02-04
The answer is C=x1*y2-x2*y1. Just for curiosity, what is a CMPSC 201C class ?

---

### Post by mengfei on 2007-02-04
Thank you so much. At my university, CMPSC 201C is a beginning programming course for potential engineers.

---

### Post by shareMenaPeace on 2007-02-04
> **gborzi said:**
> The answer is C=x1*y2-x2*y1. Just for curiosity, what is a CMPSC 201C class ?

[http://www.google.de/search?hl=de&q=CMPSC+201C&btnG=Google-Suche&meta=](http://www.google.de/search?hl=de&q=CMPSC+201C&btnG=Google-Suche&meta=)

---

### Post by mengfei on 2007-02-04
I'm having more trouble with programming...
My professor wants the program to display the numerical answers that my program computes to 12 digits. I thought he said to type something to the effect of cout.precision(12), but when I put that in, it comes up as an error. Can anyone tell me what I should be putting in?

---

### Post by mengfei on 2007-02-05
nevermind, I found that I needed to put std::setprecision(12) before the variable

---

