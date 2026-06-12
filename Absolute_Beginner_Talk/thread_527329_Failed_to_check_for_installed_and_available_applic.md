---
title: "Failed to check for installed and available applications"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Hazmat. on 2007-08-16
After attemping to install java runtime enviorment, a error occured.

Error message:
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


What do i do? :$

---

### Post by Trebaruna on 2007-08-16
Did you do what that tells you to?

---

### Post by Hazmat. on 2007-08-16
Yup, it works i had to hop onto root though, i have problems with su and sudo lol.
I did the thing it told me to do in terminal, the other part about the file i didn't do and it worked, so i'm assuming i don't have to do that....

---

### Post by onTop on 2008-06-08
I have the same problem. I've done what the error-message told me to do. Any suggestions?
Problem solved.It worked after I wrote this in the terminal: sudo apt-get update; sudo apt-get -f upgrade;

---

