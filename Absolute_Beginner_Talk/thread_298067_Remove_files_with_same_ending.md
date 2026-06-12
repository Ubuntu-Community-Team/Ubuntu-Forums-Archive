---
title: "Remove files with same ending"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by sabrina on 2006-11-12
Hi!

How do I remove all the files in a directory (and subdirectory) that is of the type ".tex~"?

---

### Post by Average Joe on 2006-11-12
Go to the right directory first, and type:
> rm -R *.tex~

---

### Post by sabrina on 2006-11-12
Thank you so much!

---

### Post by sabrina on 2006-11-12
I've just found out, that the -R doesn't work. It doesn't remove the files in the subdirectories.

fx if I'm in

/report/

and I write "rm -R *.tex~" it doesn't remove the files ending with .tex~ and laying in 

/report/differentialequations

---

### Post by Average Joe on 2006-11-12
You are right. Try:
> find . -name \*.tex~ -exec rm {} \;

---

