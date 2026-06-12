---
title: "Midnight Commander"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Gerbils on 2006-06-04
How do I install midnight commander so I can use it under dapper?
the command "sudo apt-get install mc" gives out this error:
E: Couldn't find package mc

Thanks.

---

### Post by Harleen on 2006-06-04
This package is in the universe repository, which you probably haven't enabled yet

---

### Post by Gerbils on 2006-06-04
Thanks for your quick reply.

Here is how to do it all: [https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto)

And then just type: sudo apt-get install mc

Another question. Is it, when looking at security, advised to undo the process after you are finished?

---

### Post by Harleen on 2006-06-04
The packages in universe can be regarded as safe, as they belong somehow to the standard Ubuntu distribution. But universe software won't neccessarily get security fixes. Canonical (the company behind Ubuntu) only guarantees security fixes for the main and restricted repositories.
You can get more information about the different sections here: [http://www.ubuntu.com/ubuntu/components#head-83c417468ac62506377459c6915798cdb7a24ae2](http://www.ubuntu.com/ubuntu/components#head-83c417468ac62506377459c6915798cdb7a24ae2)

---

