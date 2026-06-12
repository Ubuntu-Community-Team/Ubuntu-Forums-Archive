---
title: "gcc cjompiler"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by citizenthom on 2007-11-26
i've written a code in C to solve a math problem. i compile it using gcc but when i try and run the executable, which is called implicit, is just says "bash: implicit: command not found"  even though i'm sitting in the same directory as the executable. How can i run this executable?

---

### Post by approaching on 2007-11-26
in that directory do an ls. then ./ that command. ./ means to run in this directory. when you enter in a command it is actually looking through this PATH variable that has been set to a good default, and if you are programming in a certain directory, you may want to consider adding it to that variable (i believe it is export path ..., but you should check the man page before you do anything serious). or you could just type in the entire directory, which sucks, don't do that. so to be even more clear you would do this in the correct directory:

./whatever_your_program_is_called

---

