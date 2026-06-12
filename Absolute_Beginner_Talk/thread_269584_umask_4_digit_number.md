---
title: "umask 4 digit number?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-10-01
I am reading this "teach yourself UNIX in 24 hours" book.

The section on file permissions goes over the umask and gives a 3 digit example. when I query my sys. I get a 4 digit 0022 does anyone know how that translates?

I understand how to calculate the umask with three digits but where am I getting the fourth digit?

---

### Post by TheMono on 2006-10-02
I can't for the life of me remember the reason for this, but the upshot of it is ignore the first digit, ie work with 022

---

### Post by yaraju on 2007-07-12
Just noticed while Googling... Looks like the "0" there is supposed to 
explicitly specify that the number is Octal.
Avanish

---

