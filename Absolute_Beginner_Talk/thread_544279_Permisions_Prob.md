---
title: "Permisions Prob"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by nnjond on 2007-09-06
Howdy Do-Gooders!

I have a dual boot; Win 2000/Fiesty Fawn. All my data is on a second hd which appears at 

Location: Computer:///

Access requires me to use password. How can I alter Permisions?

Ubuntu Wannabe.

---

### Post by henriette_holm on 2007-09-06
If you're trying to access the second drive from Ubuntu you'll properly find it in /media.
Open a terminal and type:

$ cd /media


(without the $). Then look at the permissions for the path where you drive is mounted. should look something like dwrx-r-x-r-x

You can post it here.

/henriette

---

