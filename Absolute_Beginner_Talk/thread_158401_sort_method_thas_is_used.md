---
title: "sort method thas is used"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by martijn1981 on 2006-04-11
Hello,

could anyone tell me how I change the sort method that is used by linux commands, such as ls. The problem actually is that all linux commands / applications skip tokens such as _ and +. I will explain the problem by giving an example. When we have two words, say _B and A, ls will deliver the following result:
A
_B

I want this command giving me back:
_B
A

I hope I made clear my problem and that someone knows a solution!

Thankz.
Martijn

---

### Post by mvaniersel on 2006-04-11
You can pass the output of the ls command to perl, which sorts strictly ASCIIbetical. Try this: 

```
ls | perl -e 'print sort <>'
```

Since the ascii code of '_' is 95, _B will appear after A (capital, ascii 65) but before a (lowercase, ascii 97).

---

### Post by martijn1981 on 2006-04-11
[QUOTE=mvaniersel]You can pass the output of the ls command to perl, which sorts strictly ASCIIbetical. Try this: 

```
ls | perl -e 'print sort <>'
```

Since the ascii code of '_' is 95, _B will appear after A (capital, ascii 65) but before a (lowercase, ascii 97).[/QUOTE]

Thanks for your reaction. Your solution partly works. I have a large set of files which have an _ or + as prefix. I want these files at the end or begin of the list which is returned by ls. With your solution I first get the files with an +, then a number of files in alphabetical order, then a number of files which starts with an _, and after that, at the end of the list, another list of files which are alphabetically sorted. So, your solution makes is not the solution. 
And I am actually looking for a solution that is integrated in the system (e.g. used by konquerer).

---

### Post by mvaniersel on 2006-04-11
Yes, the order is according to ASCII, see the [ASCII table]("http://en.wikipedia.org/wiki/ASCII_code#ASCII_printable_characters")

Of course one could write a slightly more complicated perl line that sorts in any arbitrary order. But a solution that is integrated in the system does not exists. Your needs are too specific.

---

